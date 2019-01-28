# JNA

使用JNA的过程中也不一定会一帆风顺,比如会抛出”非法内存访问”,这时候检查一下变量是否==null。还有内存对齐的问题，当从内存进行保存的时候，如果内存对齐处理不好,就会抛出很严重的异常,导致JVM异常退出，JNA提供了四种内存对齐的方式，分别 是：ALIGN_DEFAULT、ALIGN_NONE、ALIGN_GNUC和ALIGN_MSVC。ALIGN_DEFAULT采用平台默认的对齐方 式(推荐);ALIGN_NONE是不采用对齐方式；ALIGN_GNUC为针对linux/gcc操作系统的对齐方式。ALIGN_MSVC为针对 win32/msvc架构的内存对齐方式。

    JNA也提供了一种保护机制.比如防止JNA出现异常不会导致JVM异常退出，默认是开启这个功能的，开启方式为 System.setProperty(“jna.protected”,”true”); 记得要在JNA加载dll文件之前调用，然后try {...} catch(Throwable e)异常，不过你也不要期望过高,不要以为加上这个就万事大吉,出现”非法内存访问”的时候还是会束手无策。

构造函数
          public  NotesFileObjectStruct()  {  
          super(); 
          setAlignType(Structure.ALIGN_NONE);  
          }
