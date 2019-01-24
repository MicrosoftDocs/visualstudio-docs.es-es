---
title: Adición de Azure Storage con servicios conectados en Visual Studio | Microsoft Docs
description: Adición de Azure Storage a la aplicación mediante el cuadro de diálogo de Visual Studio agregar servicios conectados
author: ghogen
manager: douge
assetId: 521ec044-ad4b-4828-8864-01decde2e758
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/26/2017
ms.author: ghogen
ms.openlocfilehash: 63b796d9c514602a40f15b5725c07b1b89787df1
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002336"
---
# <a name="adding-azure-storage-by-using-visual-studio-connected-services"></a>Adición de almacenamiento de Azure con Visual Studio Connected Services
Con Visual Studio, se puede conectar cualquiera de los siguientes a Azure Storage mediante el **agregar servicios conectados** cuadro de diálogo:

- C#servicio en la nube
- Servicio móvil de back-end de .NET
- Servicio o sitio Web ASP.NET
- Servicio de ASP.NET Core
- Servicio de Azure WebJob 

La funcionalidad del servicio conectado agrega todo el código de conexión y las referencias necesarios al proyecto y modifica los archivos de configuración de forma adecuada. 

Cuando haya finalizado, el **agregar servicios conectados** automáticamente documentación que detalla los pasos necesarios para empezar a trabajar con almacenamiento de blobs, colas, se muestra el cuadro de diálogo y las tablas.

## <a name="connect-to-azure-storage-using-the-connected-services-dialog"></a>Conectarse a Azure Storage mediante el cuadro de diálogo servicios conectados
1. Abra el proyecto en Visual Studio

1. En **el Explorador de soluciones**, haga clic en el **Connected Services** nodo y, en el menú contextual y seleccione **Agregar servicio conectado**.
   
    ![Agregar servicio conectado](./media/vs-azure-tools-connected-services-storage/IC796702.png)

1. En el **Connected Services** página, seleccione **almacenamiento en la nube con Azure Storage**.
   
    ![Agregar almacenamiento de Azure](./media/vs-azure-tools-connected-services-storage/add-azure-storage.png)

1. En el **Azure Storage** cuadro de diálogo, seleccione una cuenta de almacenamiento y seleccione **agregar**.
   
    Si necesita crear una cuenta de almacenamiento, vaya al paso siguiente. En caso contrario, vaya al paso 6.
    
    ![Agregar cuenta de almacenamiento existente al proyecto](./media/vs-azure-tools-connected-services-storage/select-azure-storage-account.png)

1. Para crear una cuenta de almacenamiento: 
   
   1. Seleccione **crear una nueva cuenta de almacenamiento** en la parte inferior del cuadro de diálogo.

   1. Rellene el **crear cuenta de almacenamiento** cuadro de diálogo y seleccione **crear**.
      
       ![Nueva cuenta de almacenamiento de Azure](./media/vs-azure-tools-connected-services-storage/create-storage-account.png)
      
   1. Cuando el **Azure Storage** muestra el cuadro de diálogo, la nueva cuenta de almacenamiento aparece en la lista. Seleccione la nueva cuenta de almacenamiento en la lista y seleccione **agregar**.

1. El almacenamiento servicio conectado aparece bajo el **referencias de servicio** nodo del proyecto.
   
## <a name="how-your-project-is-modified"></a>¿Cómo se modifica el proyecto
Cuando haya terminado, el cuadro de diálogo, Visual Studio agrega las referencias y modifica determinados archivos de configuración. Los cambios específicos dependen del tipo de proyecto: 

- Proyecto ASP.NET - [¿qué ha ocurrido? – proyectos de ASP.NET](http://go.microsoft.com/fwlink/p/?LinkId=513126)
- Proyecto de ASP.NET Core - [¿qué ha ocurrido? – proyectos de ASP.NET 5](http://go.microsoft.com/fwlink/p/?LinkId=513124) 
- Proyecto de servicio en la nube (roles web y roles de trabajo) - [¿qué ha ocurrido? – proyectos de servicio en la nube](http://go.microsoft.com/fwlink/p/?LinkId=516965)
- Proyecto de WebJob - [¿qué ha ocurrido? - proyectos de Webjobs](/azure/visual-studio/vs-storage-webjobs-what-happened)

## <a name="next-steps"></a>Pasos siguientes
- [Foro de MSDN: Azure Storage](https://social.msdn.microsoft.com/forums/azure/home?forum=windowsazuredata)
- [Blog del equipo de Microsoft Azure Storage](http://blogs.msdn.com/b/windowsazurestorage/)
- [Documentación de Azure Storage](https://docs.microsoft.com/azure/storage/)
