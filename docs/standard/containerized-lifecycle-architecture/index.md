---
title: "容器和 Docker 簡介"
description: "Microsoft 平台和工具的容器化 Docker 應用程式生命週期"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 4e79c4658492516e33efc0b33408e3d4220640f3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="introduction-to-containers-and-docker"></a><span data-ttu-id="2a6c6-104">容器和 Docker 簡介</span><span class="sxs-lookup"><span data-stu-id="2a6c6-104">Introduction to containers and Docker</span></span>

<span data-ttu-id="2a6c6-105">容器化是一種軟體開發方法，在此方法中，應用程式或服務、其相依性及其組態 (抽象化為部署資訊清單檔) 會封裝在一起，成為一個容器映像。</span><span class="sxs-lookup"><span data-stu-id="2a6c6-105">Containerization is an approach to software development in which an application or service, its dependencies, and its configuration (abstracted as deployment manifest files) are packaged together as a container image.</span></span> <span data-ttu-id="2a6c6-106">您可以將容器化應用程式當作一個單位來測試，並將它以容器映像執行個體形式部署至主機作業系統。</span><span class="sxs-lookup"><span data-stu-id="2a6c6-106">You then can test the containerized application as a unit and deploy it as a container image instance to the host operating system.</span></span>

<span data-ttu-id="2a6c6-107">就像運輸業使用標準化貨櫃以透過船隻、火車或貨車移動貨物，而不論其內的貨物，軟體容器都是標準軟體單位，可包含不同的程式碼和相依性。</span><span class="sxs-lookup"><span data-stu-id="2a6c6-107">Just as the shipping industry uses standardized containers to move goods by ship, train, or truck, regardless of the cargo within them, software containers act as a standard unit of software that can contain different code and dependencies.</span></span> <span data-ttu-id="2a6c6-108">將軟體放置到容器可讓開發人員和 IT 專業人員只需要一點修改或不需要任何修改，就能跨環境部署這些容器。</span><span class="sxs-lookup"><span data-stu-id="2a6c6-108">Placing software into containers makes it possible for developers and IT professionals to deploy those containers across environments with little or no modification.</span></span>

<span data-ttu-id="2a6c6-109">容器也可讓不同的應用程式在共用作業系統 (OS) 上彼此隔離。</span><span class="sxs-lookup"><span data-stu-id="2a6c6-109">Containers also isolate applications from one another on a shared operating system (OS).</span></span> <span data-ttu-id="2a6c6-110">容器化應用程式會在容器主機上執行，再於 OS (Linux 或 Windows) 上執行。</span><span class="sxs-lookup"><span data-stu-id="2a6c6-110">Containerized applications run on top of a container host, which in turn runs on the OS (Linux or Windows).</span></span> <span data-ttu-id="2a6c6-111">因此，容器所需空間明顯小於虛擬機器 (VM) 映像。</span><span class="sxs-lookup"><span data-stu-id="2a6c6-111">Thus, containers have a significantly smaller footprint than virtual machine (VM) images.</span></span>

<span data-ttu-id="2a6c6-112">每個容器都可以執行整個 Web 應用程式或服務，如圖 1-1 所示。</span><span class="sxs-lookup"><span data-stu-id="2a6c6-112">Each container can run an entire web application or a service, as shown in Figure 1-1.</span></span>

![](./media/image1.png)

<span data-ttu-id="2a6c6-113">圖 1-1：在容器主機上執行的多個容器</span><span class="sxs-lookup"><span data-stu-id="2a6c6-113">Figure 1-1: Multiple containers running on a container host</span></span>

<span data-ttu-id="2a6c6-114">在此範例中，Docker 主機是容器主機，而 App 1、App 2、Svc 1 和 Svc 2 是容器化應用程式或服務。</span><span class="sxs-lookup"><span data-stu-id="2a6c6-114">In this example, Docker Host is a container host, and App 1, App 2, Svc 1, and Svc 2 are containerized applications or services.</span></span>

<span data-ttu-id="2a6c6-115">您可以從容器化衍生的另一個優點是延展性。</span><span class="sxs-lookup"><span data-stu-id="2a6c6-115">Another benefit you can derive from containerization is scalability.</span></span> <span data-ttu-id="2a6c6-116">針對短期工作建立新的容器，即可更快速地擴充。</span><span class="sxs-lookup"><span data-stu-id="2a6c6-116">You can scale-out quickly by creating new containers for short-term tasks.</span></span> <span data-ttu-id="2a6c6-117">從應用程式的觀點來看，「具現化映像」(建立容器) 類似於具現化處理序 (例如服務或 Web 應用程式)。</span><span class="sxs-lookup"><span data-stu-id="2a6c6-117">From an application point of view, *instantiating an image* (creating a container) is similar to instantiating a process like a service or web app.</span></span> <span data-ttu-id="2a6c6-118">不過，為了可靠起見，當您在多部主機伺服器之間執行相同映像的多個執行個體時，您通常需要在不同的主機伺服器或 VM 中，或是不同的容錯網域中，執行各個容器 (映像執行個體)。</span><span class="sxs-lookup"><span data-stu-id="2a6c6-118">For reliability, however, when you run multiple instances of the same image across multiple host servers, you typically want each container (image instance) to run in a different host server or VM in different fault domains.</span></span>

<span data-ttu-id="2a6c6-119">簡單來說，容器在整個應用程式生命週期工作流程中，提供隔離、可攜性、彈性、延展性和控制能力等優點。</span><span class="sxs-lookup"><span data-stu-id="2a6c6-119">In short, containers offer the benefits of isolation, portability, agility, scalability, and control across the entire application life cycle workflow.</span></span> <span data-ttu-id="2a6c6-120">最重要的優點是為開發與作業提供隔離。</span><span class="sxs-lookup"><span data-stu-id="2a6c6-120">The most important benefit is the isolation provided between Dev and Ops.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="2a6c6-121">[下一個] (what-is-docker.md)</span><span class="sxs-lookup"><span data-stu-id="2a6c6-121">[Next] (what-is-docker.md)</span></span>