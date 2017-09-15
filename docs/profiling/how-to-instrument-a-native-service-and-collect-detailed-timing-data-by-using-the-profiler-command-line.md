---
title: 'How to: Instrument a Native Service and Collect Detailed Timing Data by Using the Profiler Command Line | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dfe58b39-63f8-4a87-ab3a-2b5b14faa8d0
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 7c87490f8e4ad01df8761ebb2afee0b2d3744fe2
ms.openlocfilehash: df078601b46817b46f885cb2a20248a5612850f6
ms.contentlocale: pt-br
ms.lasthandoff: 08/31/2017

---
# <a name="how-to-instrument-a-native-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line"></a>How to: Instrument a Native Service and Collect Detailed Timing Data by Using the Profiler Command Line
This topic describes how to use [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profiling Tools command-line tools to instrument a native (C/C++) service and collect detailed timing data.  
  
> [!NOTE]
>  You cannot profile a service with the instrumentation method if the service cannot be restarted after the computer starts, such a service that start only when the operating system starts.  
>   
>  Command-line tools of the Profiling Tools are located in the \Team Tools\Performance Tools subdirectory of the [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] installation directory. On 64 bit computers, both 64 bit and 32 bit versions of the tools are available. To use the profiler command-line tools, you must add the tools path to the PATH environment variable of the command prompt window or add it to the command itself. For more information, see [Specifying the Path to Command Line Tools](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 To collect detailed timing data from a native service by using the instrumentation method, you use the [VSInstr.exe](../profiling/vsinstr.md) tool to generate an instrumented version of the component. You then replace the non-instrumented version of the service with the instrumented version, making sure that the service is configured to start manually. You then start the profiler.  
  
 When the service is started, timing data is automatically collected to a data file. You can pause and resume data collection during the profiling session.  
  
 To end a profiling session, you turn off the service and then explicitly shut down the profiler.  
  
## <a name="starting-the-application-with-the-profiler"></a>Starting the Application with the Profiler  
  
#### <a name="to-start-profiling-a-native-service"></a>To start profiling a native service  
  
1.  Open a command prompt window.  
  
2.  Use the **VSInstr** tool to generate an instrumented version of the service binary.  
  
3.  Replace the original binary with the instrumented version. In Windows Service Control Manager, make sure that the service Startup Type is set to Manual.  
  
4.  Start the profiler. Type:  
  
     **VSPerfCmd** [/start](../profiling/start.md) **:trace**  [/output](../profiling/output.md) **:** `OutputFile` [`Options`]  
  
    -   The **/start:trace** option initializes the profiler.  
  
    -   The **/output:**`OutputFile` option is required with **/start**. `OutputFile` specifies the name and location of the profiling data (.vsp) file.  
  
     You can use any of the following options with the **/start:trace** option.  
  
    > [!NOTE]
    >  The **/user** and **/crosssession** options are usually required for ASP.NET applications.  
  
    |Option|Description|  
    |------------|-----------------|  
    |[/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|Specifies the domain and user name of the account that owns the ASP.NET worker process. This option is required if the process is running as a user other than the logged on user. The process owner is listed in the User Name column on the Processes tab of Windows Task Manager.|  
    |[/crosssession](../profiling/crosssession.md)|Enables profiling of processes in other logon sessions. This option is required if the ASP.NET application is running in a different session. The session id is listed in the Session ID column on the Processes tab of Windows Task Manager. **/CS** can be specified as an abbreviation for **/crosssession**.|  
    |[/waitstart](../profiling/waitstart.md)[**:**`Interval`]|Specifies the number of seconds to wait for the profiler to initialize before it returns an error. If `Interval` is not specified, the profiler waits indefinitely. By default, **/start** returns immediately.|  
    |[/globaloff](../profiling/globalon-and-globaloff.md)|To start the profiler with data collection paused, add the **/globaloff** option to the **/start** command line. Use **/globalon** to resume profiling.|  
    |[/counter](../profiling/counter.md) **:** `Config`|Collects information from the processor performance counter specified in Config. Counter information is added to the data collected at each profiling event.|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Specifies a Windows performance counter to be collected during profiling.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Use with **/wincounter** only. Specifies the number of milliseconds between Windows performance counter collection events. Default is 500 ms.|  
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|Specifies an Event Tracing for Windows (ETW) event to be collected during profiling. ETW events are collected in a separate (.etl) file.|  
  
5.  Start the service from Service Control Manager.  
  
## <a name="controlling-data-collection"></a>Controlling Data Collection  
 When the service is running, you can use **VSPerfCmd.exe** options to start and stop the writing of data to the profiler data file. Controlling data collection enables you to collect data for a specific part of program execution, such as starting or shutting down the service.  
  
#### <a name="to-start-and-stop-data-collection"></a>To start and stop data collection  
  
-   The following pairs of **VSPerfCmd** options start and stop data collection. Specify each option on a separate command line. You can turn data collection on and off multiple times.  
  
    |Option|Description|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Starts (**/globalon**) or stops (**/globaloff**) data collection for all processes.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Starts (**/processon**) or stops (**/processoff**) data collection for the process specified by the process ID (`PID`).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Starts (**/threadon**) or stops (**/threadoff**) data collection for the thread specified by the thread ID (`TID`).|  
  
## <a name="ending-the-profiling-session"></a>Ending the Profiling Session  
 To end a profiling session, stop the service that is running the instrumented component, and then call the **VSPerfCmd**[/shutdown](../profiling/shutdown.md) option to turn the profiler off and close the profiling data file.  
  
#### <a name="to-end-a-profiling-session"></a>To end a profiling session  
  
1.  Stop the service from Service Control Manager.  
  
2.  Shut down the profiler. Type:  
  
     **VSPerfCmd /shutdown**  
  
3.  Replace the instrumented module with the original. If necessary, reconfigure the Startup Type of the service.  
  
## <a name="see-also"></a>See Also  
 [Profiling Services](../profiling/command-line-profiling-of-services.md)   
 [Instrumentation Method Data Views](../profiling/instrumentation-method-data-views.md)