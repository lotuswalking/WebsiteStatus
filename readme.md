日志方法:

Serilog.aspNetCore

Serilog.sink.file

在program.cs中

1.增加引用using Serilog;

2.Log.Logger = new LoggerConfiguration()

                .MinimumLevel.Debug()

                .MinimumLevel.Override("Microsoft", Serilog.Events.LogEventLevel.Warning)

                .Enrich.FromLogContext()

                .WriteTo.File(@"c:\temp\workerService\LogFile.txt")

                .CreateLogger();

3.程序异常退出时:Log.CloseAndFlush();

4. CreateHostBuilder的时候加入.UseSerilog()方法

Microsoft.Extensions.Hosting.WindowsServices

CreateHostBuilder的时候加入.UseWindowsService()方法

添加为window 服务

SC.exe create/delete
