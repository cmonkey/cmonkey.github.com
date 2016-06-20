---
layout: post
title: "CountDownLatchWating"
date: 2016-06-20T06:26:50+00:00
---

    import java.util.concurrent.CountDownLatch;
    import java.util.concurrent.ExecutorService;
    import java.util.concurrent.Executors;

    public class CountDownLatchWating {

        private final static Logger logger = LoggerFactory.getLogger(CountDownLatchWating.class);

        public static void main(String[] args) {
            ExecutorService service = Executors.newCachedThreadPool();
            
            final CountDownLatch cdl = new CountDownLatch(3);
            
            service.execute(()-> {
                try {
                    logger.info("working...");

                    cdl.await();

                } catch (InterruptedException e) {
                    e.printStackTrace();
                    logger.error("Exception = {}", e);
                }
            });
            
            for (int i = 0; i < 3; i++) {
                final int tid = i;
                service.execute(() -> {
                    try {
                        Thread.sleep((long) (Math.random() * 5000));

                        cdl.countDown();

                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                });
            }
            
            service.shutdown();
        }

    }

