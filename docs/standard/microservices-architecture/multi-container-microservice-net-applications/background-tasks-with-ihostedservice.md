---
title: "在微服務中使用 IHostedService 和 BackgroundService 類別實作背景工作"
description: "容器化 .NET 應用程式的 .NET 微服務架構 | 在微服務中使用 IHostedService 和 BackgroundService 類別實作背景工作"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d60a4590682b79a9f8ac57afee09884b7edd1f98
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a><span data-ttu-id="7ffe7-104">在微服務中使用 IHostedService 和 BackgroundService 類別實作背景工作</span><span class="sxs-lookup"><span data-stu-id="7ffe7-104">Implement background tasks in microservices with IHostedService and the BackgroundService class</span></span>

<span data-ttu-id="7ffe7-105">在微服務應用程式或任何類型的應用程式中，背景工作和已排定工作最後是您可能需要實作的工作。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-105">Background tasks and scheduled jobs are something you might need to implement, eventually, in a microservice based application or in any kind of application.</span></span> <span data-ttu-id="7ffe7-106">使用微服務架構的差異在於您可以實作單一微服務程序/容器來裝載這些背景工作，讓您可以視需要進行相應減少/相應增加，或者甚至可以確定它執行該微服務程序/容器的單一執行個體。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-106">The difference when using a microservices architecture is that you can implement a single microservice process/container for hosting these background tasks so you can scale it down/up as you need or you can even make sure that it runs a single instance of that microservice process/container.</span></span>

<span data-ttu-id="7ffe7-107">從一般觀點而言，在 .NET Core 中，我們將這些類型的工作稱為「託管服務」，因為它們是您在主機/應用程式/微服務內裝載的服務/邏輯。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-107">From a generic point of view, in .NET Core we called these type of tasks Hosted Services, because they are services/logic that you host within your host/application/microservice.</span></span> <span data-ttu-id="7ffe7-108">請注意，在此情況下，託管服務就只是具有背景工作邏輯的類別。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-108">Note that in this case, the hosted service simply means a class with the background task logic.</span></span>

<span data-ttu-id="7ffe7-109">自 .NET Core 2.0 開始，此架構提供名為 <xref:Microsoft.Extensions.Hosting.IHostedService> 的新介面，協助您輕鬆地實作託管服務。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-109">Since .NET Core 2.0, the framework provides a new interface named <xref:Microsoft.Extensions.Hosting.IHostedService> helping you to easily implement hosted services.</span></span> <span data-ttu-id="7ffe7-110">基本概念是您可以註冊多個背景工作 (託管服務)，以在 WebHost 或主機執行時於背景中執行，在下圖所示。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-110">The basic idea is that you can register multiple background tasks (hosted services), that run in the background while your web host or host is running, as shown in the image below.</span></span>

![](./media/image26.png)

<span data-ttu-id="7ffe7-111">**圖 8-25.**</span><span class="sxs-lookup"><span data-stu-id="7ffe7-111">**Figure 8-25.**</span></span> <span data-ttu-id="7ffe7-112">在 WebHost 與主機中使用 IHostedService</span><span class="sxs-lookup"><span data-stu-id="7ffe7-112">Using IHostedService in a WebHost vs. a Host</span></span>

<span data-ttu-id="7ffe7-113">請注意 `WebHost` 與 `Host` 之間的差異。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-113">Note the difference made between `WebHost` and `Host`.</span></span> <span data-ttu-id="7ffe7-114">ASP.NET Core 2.0 中的 `WebHost` (實作 `IWebHost` 的基底類別) 是用來將 HTTP 伺服器功能提供給程序的基礎結構成品，就像您是實作 MVC Web 應用程式或 Web API 服務一樣。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-114">A `WebHost` (base class implementing `IWebHost`) in ASP.NET Core 2.0 is the infrastructure artifact you use to provide HTTP server features to your process, such as if you are implementing an MVC web app or Web API service.</span></span> <span data-ttu-id="7ffe7-115">它會提供 ASP.NET Core 中的所有新基礎結構優點，讓您可以使用相依性插入、在 HTTP 管道中插入中介軟體等等，以及精確地使用這些 `IHostedServices` 進行背景工作。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-115">It provides all the new infrastructure goodness in ASP.NET Core, enabling you to use dependency injection, insert middlewares in the HTTP pipeline, etc. and precisely use these `IHostedServices` for background tasks.</span></span>

<span data-ttu-id="7ffe7-116">不過，`Host` (實作 `IHost` 的基底類別) 是 .NET Core 2.1 中的新功能。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-116">A `Host` (base class implementing `IHost`), however, is something new in .NET Core 2.1.</span></span> <span data-ttu-id="7ffe7-117">基本上，`Host` 可讓您擁有與 `WebHost` 類似的基礎結構 (相依性插入、託管服務等等)，但在此情況下，您只想要有主機的簡單且輕量程序，而不想要有與 MVC、Web API 或 HTTP 伺服器功能有關的程序。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-117">Basically, a `Host` allows you to have a similar infrastructure than what you have with `WebHost` (dependency injection, hosted services, etc.), but in this case, you just want to have a simple and lighter process as the host, with nothing related to MVC, Web API or HTTP server features.</span></span>

<span data-ttu-id="7ffe7-118">因此，您可以選擇並使用 IHost 建立特殊化託管程序以處理託管服務，但不處理其他項目 (例如其製作目的只是要裝載 `IHostedServices` 的微服務)，也可以擴充現有 ASP.NET Core `WebHost` (例如現有 ASP.NET Core Web API 或 MVC 應用程式)。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-118">Therefore, you can choose and either create a specialized host-process with IHost to handle the hosted services and nothing else, such a microservice made just for hosting the `IHostedServices`, or you can alternatevely extend an existing ASP.NET Core `WebHost`, such as an existing ASP.NET Core Web API or MVC app.</span></span> 

<span data-ttu-id="7ffe7-119">根據您的商務和延展性需求，每種方法都有其優缺點。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-119">Each approach has pros and cons depending on your business and scalability needs.</span></span> <span data-ttu-id="7ffe7-120">底線基本上是您的背景工作不需要處理您應該使用的 HTTP (IWebHost) 和 IHost (在 .NET Core 2.1 中可用時)。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-120">The bottom line is basically that if your background tasks have nothing to do with HTTP (IWebHost) you should use and IHost, when available in .NET Core 2.1.</span></span>

## <a name="registering-hosted-services-in-your-webhost-or-host"></a><span data-ttu-id="7ffe7-121">在 WebHost 或主機中註冊託管服務</span><span class="sxs-lookup"><span data-stu-id="7ffe7-121">Registering hosted services in your WebHost or Host</span></span>

<span data-ttu-id="7ffe7-122">讓我們更深入了解 `IHostedService` 介面，因為它在 `WebHost` 或 `Host` 中的使用相當類似。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-122">Let’s drill down further on the `IHostedService` interface since its usage is pretty similar in a `WebHost` or in a `Host`.</span></span> 

<span data-ttu-id="7ffe7-123">SignalR 是使用託管服務之成品的一個範例，但您也可以將它用於下列更簡單的事項：</span><span class="sxs-lookup"><span data-stu-id="7ffe7-123">SignalR is one example of an artifact using hosted services, but you can also use it for much simpler things like:</span></span>

-   <span data-ttu-id="7ffe7-124">輪詢資料庫以找出變更的背景工作。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-124">A background task polling a database looking for changes.</span></span>
-   <span data-ttu-id="7ffe7-125">定期更新某個快取的已排定工作。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-125">A scheduled task updating some cache periodically.</span></span>
-   <span data-ttu-id="7ffe7-126">允許在背景執行緒上執行工作的 QueueBackgroundWorkItem 實作。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-126">An implementation of QueueBackgroundWorkItem that allows a task to be executed on a background thread.</span></span>
-   <span data-ttu-id="7ffe7-127">在共用 `ILogger` 這類通用服務時，於 Web 應用程式背景處理來自佇列的訊息。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-127">Processing messages from a message queue in the background of a web app while sharing common services such as `ILogger`.</span></span>
-   <span data-ttu-id="7ffe7-128">使用 `Task.Run()` 啟動的背景工作。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-128">A background task started with `Task.Run()`.</span></span>

<span data-ttu-id="7ffe7-129">您基本上可以根據 IHostedService，將其中任何動作卸載至背景工作。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-129">You can basically offload any of those actions to a background task based on IHostedService.</span></span>

<span data-ttu-id="7ffe7-130">將一或多個 `IHostedServices` 新增至 `WebHost` 或 `Host` 的方法是透過 ASP.NET Core `WebHost` (或 .NET Core 2.1 中的 `Host`) 中的標準 DI (相依性插入) 註冊它們。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-130">The way you add one or multiple `IHostedServices` into your `WebHost` or `Host` is by registering them up through the standard DI (dependency injection) in an ASP.NET Core `WebHost` (or in a `Host` in .NET Core 2.1).</span></span> <span data-ttu-id="7ffe7-131">基本上，您必須在 `Startup` 類別的熟悉 `ConfigureServices()` 方法內註冊託管服務，如典型 ASP.NET WebHost 中的下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-131">Basically, you have to register the hosted services within the familiar `ConfigureServices()` method of the `Startup` class, as in the following code from a typical ASP.NET WebHost.</span></span> 

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{            
    //Other DI registrations;

    // Register Hosted Services
    services.AddSingleton<IHostedService, GracePeriodManagerService>();
    services.AddSingleton<IHostedService, MyHostedServiceB>();
    services.AddSingleton<IHostedService, MyHostedServiceC>();
    //...
}
```

<span data-ttu-id="7ffe7-132">在該程式碼中，`GracePeriodManagerService` 託管服務是 eShopOnContainers 中來自 Ordering 商務微服務的真正程式碼，另兩個就只是兩個其他範例。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-132">In that code, the `GracePeriodManagerService` hosted service is real code from the Ordering business microservice in eShopOnContainers, while the other two are just two additional samples.</span></span>

<span data-ttu-id="7ffe7-133">`IHostedService` 背景工作執行會與應用程式 (就此而言，是主機或微服務) 存留期一致。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-133">The `IHostedService` background task execution is coordinated with the lifetime of the application (host or microservice, for that matter).</span></span> <span data-ttu-id="7ffe7-134">您在應用程式啟動時註冊工作，並且在關閉應用程式時，有機會依正常程序進行某個動作或清除。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-134">You register tasks when the application starts and you have the opportunity to do some graceful action or clean-up when the application is shutting down.</span></span>

<span data-ttu-id="7ffe7-135">不使用 `IHostedService`，您還是一律可以啟動背景執行緒來執行任何工作。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-135">Without using `IHostedService`, you could always start a background thread to run any task.</span></span> <span data-ttu-id="7ffe7-136">差異就在於只終止該執行緒而沒有機會依正常程序執行清除動作時的應用程式關閉時間。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-136">The difference is precisely at the app’s shutdown time when that thread would simply be killed without having the opportunity to run graceful clean-up actions.</span></span>


## <a name="the-ihostedservice-interface"></a><span data-ttu-id="7ffe7-137">IHostedService 介面</span><span class="sxs-lookup"><span data-stu-id="7ffe7-137">The IHostedService interface</span></span>

<span data-ttu-id="7ffe7-138">註冊 `IHostedService` 時，.NET Core 將會在應用程式啟動和停止期間分別呼叫 `IHostedService` 型別的 `StartAsync()` 和 `StopAsync()` 方法。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-138">When you register an `IHostedService`, .NET Core will call the `StartAsync()` and `StopAsync()` methods of your `IHostedService` type during application start and stop respectively.</span></span> <span data-ttu-id="7ffe7-139">具體而言，在啟動伺服器之後會呼叫啟動，並觸發 `IApplicationLifetime.ApplicationStarted`。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-139">Specifically, start is called after the server has started and `IApplicationLifetime.ApplicationStarted` is triggered.</span></span>

<span data-ttu-id="7ffe7-140">.NET Core 中所定義的 `IHostedService` 如下。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-140">The `IHostedService` as defined in .NET Core, looks like the following.</span></span>

```csharp
namespace Microsoft.Extensions.Hosting
{
    //
    // Summary:
    //     Defines methods for objects that are managed by the host.
    public interface IHostedService
    {
        //
        // Summary:
        // Triggered when the application host is ready to start the service.
        Task StartAsync(CancellationToken cancellationToken);
        //
        // Summary:
        // Triggered when the application host is performing a graceful shutdown.
        Task StopAsync(CancellationToken cancellationToken);
    }
}
```
<span data-ttu-id="7ffe7-141">假設您可以建立多個 IHostedService 實作，並在 `ConfigureService()` 方法中將它們註冊至 DI 容器，如前所示。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-141">As you can imagine, you can create multiple implementations of IHostedService and register them at the `ConfigureService()` method into the DI container, as shown previously.</span></span> <span data-ttu-id="7ffe7-142">將會啟動與停止所有這些託管服務以及應用程式/微服務。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-142">All those hosted services will be started and stopped along with the application/microservice.</span></span>

<span data-ttu-id="7ffe7-143">身為開發人員，您負責在主機觸發 `StopAsync()` 方法時處理停止動作或服務。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-143">As a developer, you are responsible for handling the stopping action or your services when `StopAsync()` method is triggered by the host.</span></span>

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a><span data-ttu-id="7ffe7-144">使用衍生自 BackgroundService 基底類別的自訂託管服務類別來實作 IHostedService</span><span class="sxs-lookup"><span data-stu-id="7ffe7-144">Implementing IHostedService with a custom hosted service class deriving from the BackgroundService base class</span></span>

<span data-ttu-id="7ffe7-145">您可以繼續並從頭開始建立自訂託管服務類別，並實作 `IHostedService`，就像使用 .NET Core 2.0 時所需執行的作業。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-145">You could go ahead and create you custom hosted service class from scratch and implement the `IHostedService`, as you need to do when using .NET Core 2.0.</span></span> 

<span data-ttu-id="7ffe7-146">不過，因為大部分背景工作都會有與取消權杖管理和其他典型作業相關的類似需求，所以 .NET Core 2.1 將提供您可以從中衍生且名為 BackgroundService 的極便利抽象基底類別。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-146">However, since most background tasks will have similar needs in regard to the cancellation tokens management and other tipical operations, .NET Core 2.1 will be providing a very convenient abstract base class you can derive from, named BackgroundService.</span></span>

<span data-ttu-id="7ffe7-147">該類別提供設定背景工作所需的主要工作。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-147">That class provides the main work needed to set up the background task.</span></span> <span data-ttu-id="7ffe7-148">請注意，此類別會在 .NET Core 2.1 程式庫中，因此您不需要撰寫它。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-148">Note that this class will come in the .NET Core 2.1 library so you don’t need to write it.</span></span>

<span data-ttu-id="7ffe7-149">不過，進行這項撰寫時，尚未發行 .NET Core 2.1。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-149">However, as of the time of this writing, .NET Core 2.1 has not been released.</span></span> <span data-ttu-id="7ffe7-150">因此，在目前使用 .NET Core 2.0 的 eShopOnContainers 中，我們只會暫時從 .NET Core 2.1 開放原始碼存放庫納入該類別 (不需要開放原始碼授權以外的任何專屬授權)，因為它與 .NET Core 2.0 中的目前 IHostedService 介面相容。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-150">Therefore, in eShopOnContainers which is currently using .NET Core 2.0, we are just temporally incorporating that class from the .NET Core 2.1 open-source repo (no need of any proprietary license other than the open-source license) because it is compatible with the current IHostedService interface in .NET Core 2.0.</span></span> <span data-ttu-id="7ffe7-151">發行 .NET Core 2.1 時，您只需要指向正確的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-151">When .NET Core 2.1 is released, you’ll just need to point to the right NuGet package.</span></span>

<span data-ttu-id="7ffe7-152">下個程式碼是 .NET Core 2.1 中所實作的抽象 BackgroundService 基底類別。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-152">The next code is the abstract BackgroundService base class as implemented in .NET Core 2.1.</span></span>

```csharp
// Copyright (c) .NET Foundation. Licensed under the Apache License, Version 2.0. 
/// <summary>
/// Base class for implementing a long running <see cref="IHostedService"/>.
/// </summary>
public abstract class BackgroundService : IHostedService, IDisposable
{
    private Task _executingTask;
    private readonly CancellationTokenSource _stoppingCts = 
                                                   new CancellationTokenSource();

    protected abstract Task ExecuteAsync(CancellationToken stoppingToken);

    public virtual Task StartAsync(CancellationToken cancellationToken)
    {
        // Store the task we're executing
        _executingTask = ExecuteAsync(_stoppingCts.Token);

        // If the task is completed then return it, 
        // this will bubble cancellation and failure to the caller
        if (_executingTask.IsCompleted)
        {
            return _executingTask;
        }

        // Otherwise it's running
        return Task.CompletedTask;
    }
    
    public virtual async Task StopAsync(CancellationToken cancellationToken)
    {
        // Stop called without start
        if (_executingTask == null)
        {
            return;
        }

        try
        {
            // Signal cancellation to the executing method
            _stoppingCts.Cancel();
        }
        finally
        {
            // Wait until the task completes or the stop token triggers
            await Task.WhenAny(_executingTask, Task.Delay(Timeout.Infinite,
                                                          cancellationToken));
        }

    }

    public virtual void Dispose()
    {
        _stoppingCts.Cancel();
    }
}
```

<span data-ttu-id="7ffe7-153">衍生自上一個抽象基底類別時，基於繼承的實作，您只需要在自己的自訂託管服務類別中實作 `ExecuteAsync()` 方法，如 eShopOnContainers 中的下列簡化程式碼所示，而此程式碼會輪詢資料庫並視需要將整合事件發佈至事件匯流排。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-153">When deriving from the previous abstract base class, thanks to that inherited implementation, you just need to implement the `ExecuteAsync()` method in your own custom hosted service class, as in the following simplified code from eShopOnContainers which is polling a database and publishing integration events into the Event Bus when needed.</span></span>

```csharp
public class GracePeriodManagerService : BackgroundService
{        
    private readonly ILogger<GracePeriodManagerService> _logger;
    private readonly OrderingBackgroundSettings _settings;

    private readonly IEventBus _eventBus;

    public GracePeriodManagerService(IOptions<OrderingBackgroundSettings> settings,
                                     IEventBus eventBus,
                                     ILogger<GracePeriodManagerService> logger)
        {
            //Constructor’s parameters validations...       
        }

        protected override async Task ExecuteAsync(CancellationToken stoppingToken)
        {
            _logger.LogDebug($"GracePeriodManagerService is starting.");

            stoppingToken.Register(() => 
                    _logger.LogDebug($" GracePeriod background task is stopping."));

            while (!stoppingToken.IsCancellationRequested)
            {
                _logger.LogDebug($"GracePeriod task doing background work.");

                // This eShopOnContainers method is quering a database table 
                // and publishing events into the Event Bus (RabbitMS / ServiceBus)
                CheckConfirmedGracePeriodOrders();

                await Task.Delay(_settings.CheckUpdateTime, stoppingToken);
            }
            
            _logger.LogDebug($"GracePeriod background task is stopping.");

        }

        protected override async Task StopAsync (CancellationToken stoppingToken)
        {
               // Run your graceful clean-up actions
        }
}
```

<span data-ttu-id="7ffe7-154">在 eShopOnContainers 這個特定狀況下，它會執行應用程式方法來查詢可尋找具有特定狀態之訂單的資料庫表格，以及在套用變更時，透過事件匯流排發行整合事件 (在其下，它可以使用 RabbitMQ 或 Azure 服務匯流排)。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-154">In this specific case for eShopOnContainers, it is executing an application method which is quering a database table looking for orders with a specific state and when applying changes, it is publishing integration events through the event bus (underneath it can be using RabbitMQ or Azure Service Bus).</span></span> 

<span data-ttu-id="7ffe7-155">當然，您可以改為執行任何其他商務背景工作。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-155">Of course, you could run any other business background task, instead.</span></span>

<span data-ttu-id="7ffe7-156">取消權杖預設會設定 5 秒的逾時，但您可以在使用 `IWebHostBuilder` 的 `UseShutdownTimeout` 延伸模組建置 `WebHost` 時變更該值。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-156">By default, the cancellation token is set with a 5 second timeout, although you can change that value when building your `WebHost` using the `UseShutdownTimeout` extension of the `IWebHostBuilder`.</span></span> <span data-ttu-id="7ffe7-157">這表示，我們的服務應該在 5 秒內取消，否則就會更突然地終止。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-157">This means that our service is expected to cancel within 5 seconds otherwise it will be more abruptly killed.</span></span>

<span data-ttu-id="7ffe7-158">下列程式碼會將該時間變更為 10 秒。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-158">The following code would be changing that time to 10 seconds.</span></span>

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a><span data-ttu-id="7ffe7-159">摘要類別圖表</span><span class="sxs-lookup"><span data-stu-id="7ffe7-159">Summary class diagram</span></span>

<span data-ttu-id="7ffe7-160">下圖 8-26 顯示在實作 IHostedServices 時所涉及之類別和介面的視覺效果摘要。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-160">The following image 8-26 shows a visual summary of the classes and interfaced involved when implementing IHostedServices.</span></span>
 
![](./media/image27.png)

<span data-ttu-id="7ffe7-161">**圖 8-26.**</span><span class="sxs-lookup"><span data-stu-id="7ffe7-161">**Figure 8-26.**</span></span> <span data-ttu-id="7ffe7-162">類別圖表，顯示多個與 IHostedService 相關的類別和介面</span><span class="sxs-lookup"><span data-stu-id="7ffe7-162">Class diagram showing the multiple classes and interfaces related to IHostedService</span></span>

### <a name="deployment-considerations-and-takeaways"></a><span data-ttu-id="7ffe7-163">部署考量和心得</span><span class="sxs-lookup"><span data-stu-id="7ffe7-163">Deployment considerations and takeaways</span></span>

<span data-ttu-id="7ffe7-164">請務必注意 ASP.NET Core `WebHost` 或 .NET Core `Host` 的部署方式可能會影響最後的解決方案。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-164">It is important to note that the way you deploy your ASP.NET Core `WebHost` or .NET Core `Host` might impact the final solution.</span></span> <span data-ttu-id="7ffe7-165">例如，如果您在 IIS 上部署 `WebHost` 或一般 Azure App Service，則可能會因應用程式集區回收而關閉主機。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-165">For instance, if you deploy your `WebHost` on IIS or a regular Azure App Service, your host can be shut down because of app pool recycles.</span></span> <span data-ttu-id="7ffe7-166">但是，如果您要將主機當成容器部署至 Kubernetes 或 Service Fabric 這類協調器，則可以控制保證的主機即時執行個體數目。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-166">But if you are deploying your host as a container into an orchestrator like Kubernetes or Service Fabric, you can control the assured number of live instances of your host.</span></span> <span data-ttu-id="7ffe7-167">此外，您可以考慮在雲端中使用其他方法，特別是針對這些案例 (例如 Azure Functions)。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-167">In addition, you could consider other approaches in the cloud especially made for these scenarios, like Azure Functions.</span></span> 

<span data-ttu-id="7ffe7-168">但即使針對部署至應用程式集區的 `WebHost`，有些重新擴展或排清應用程式記憶體中快取的情況可能仍然會發生。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-168">But even for a `WebHost` deployed into an app pool, there are scenarios like repopulating or flushing application’s in-memory cache, that would be still applicable.</span></span>

<span data-ttu-id="7ffe7-169">`IHostedService` 介面提供一種便利方式可在 ASP.NET Core Web 應用程式 (於 .NET Core 2.0 中) 或任何程序/主機 (使用 `IHost` 在 .NET Core 2.1 中啟動) 中啟動背景工作。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-169">The `IHostedService` interface provides a convenient way to start background tasks in an ASP.NET Core web application (in .NET Core 2.0) or in any process/host (starting in .NET Core 2.1 with `IHost`).</span></span> <span data-ttu-id="7ffe7-170">它的主要優點是，在主機本身正在關機時，您可以依正常程序取消清除背景工作的程式碼。</span><span class="sxs-lookup"><span data-stu-id="7ffe7-170">Its main benefit is the opportunity you get with the graceful cancellation to clean-up code of your background tasks when the host itself is shutting down.</span></span>


#### <a name="additional-resources"></a><span data-ttu-id="7ffe7-171">其他資源</span><span class="sxs-lookup"><span data-stu-id="7ffe7-171">Additional resources</span></span>

-   <span data-ttu-id="7ffe7-172">**在 ASP.NET Core/Standard 2.0 中建置已排定工作**</span><span class="sxs-lookup"><span data-stu-id="7ffe7-172">**Building a scheduled task in ASP.NET Core/Standard 2.0**</span></span> 

    [<span data-ttu-id="7ffe7-173">*https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html*</span><span class="sxs-lookup"><span data-stu-id="7ffe7-173">*https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html*</span></span>](https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html)

-   <span data-ttu-id="7ffe7-174">**在 ASP.NET Core 2.0 中實作 IHostedService**</span><span class="sxs-lookup"><span data-stu-id="7ffe7-174">**Implementing IHostedService in ASP.NET Core 2.0**</span></span> 

    [<span data-ttu-id="7ffe7-175">*https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice*</span><span class="sxs-lookup"><span data-stu-id="7ffe7-175">*https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice*</span></span>](https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice)

-   <span data-ttu-id="7ffe7-176">**ASP.NET Core 2.1 託管範例**</span><span class="sxs-lookup"><span data-stu-id="7ffe7-176">**ASP.NET Core 2.1 Hosting samples**</span></span> 

    [<span data-ttu-id="7ffe7-177">*https://github.com/aspnet/Hosting/tree/dev/samples/GenericHostSample*</span><span class="sxs-lookup"><span data-stu-id="7ffe7-177">*https://github.com/aspnet/Hosting/tree/dev/samples/GenericHostSample*</span></span>](https://github.com/aspnet/Hosting/tree/dev/samples/GenericHostSample)



>[!div class="step-by-step"]
<span data-ttu-id="7ffe7-178">[上一個] (test-aspnet-core-services-web-apps.md) [下一個] (../microservice-ddd-cqrs-patterns/index.md)</span><span class="sxs-lookup"><span data-stu-id="7ffe7-178">[Previous] (test-aspnet-core-services-web-apps.md) [Next] (../microservice-ddd-cqrs-patterns/index.md)</span></span>