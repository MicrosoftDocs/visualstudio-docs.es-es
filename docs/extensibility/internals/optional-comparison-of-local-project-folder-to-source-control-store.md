---
title: "Comparar la carpeta del proyecto para el almacén de Control de código fuente | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: cbf4e9f2ccbe895db79115949818345c62245f71
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Comparación opcional de la carpeta del proyecto Local para el almacén de Control de código fuente
En origen controlar 1.2 de API de complemento se lleva a cabo la comparación entre la carpeta de proyecto local y el control de código fuente mediante el uso de las funciones [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) y [SccDirDiff](../../extensibility/sccdirdiff-function.md).  
  
 Dentro de **el Explorador de soluciones**, si se selecciona una carpeta en lugar de un archivo individual, el **comparar versiones** , invoca el nuevo menú contextual [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) y [ SccDirDiff](../../extensibility/sccdirdiff-function.md) en el complemento de control de código fuente.  
  
## <a name="new-capability-flags"></a>Nuevos indicadores de capacidad  
 `SCC_CAP_DIRECTORYDIFF`  
  
 `SCC_CAP_DIRECTORYCHECKOUT`  
  
## <a name="new-functions"></a>Nuevas funciones  
 [SccDirDiff](../../extensibility/sccdirdiff-function.md)  
  
 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)  
  
 El `SccDirQueryInfo` función se llama antes de `SccDirDiff` para determinar si el directorio de trabajo es controlado por código fuente. El `SccDirDiff` función muestra las diferencias entre el directorio local actual y la carpeta de control de código fuente correspondiente. Este comando pide el complemento para mostrar la lista de cambios en el directorio de control de código fuente. Un complemento de control de código fuente proporciona su propia interfaz de usuario para mostrar las diferencias.  
  
> [!NOTE]
>  Esta función utiliza los mismos marcadores de comando como [SccDiff](../../extensibility/sccdiff-function.md). Como un proveedor de complemento de control de código fuente, puede que no admita la operación de "diff rápido" para los directorios.  
  
## <a name="see-also"></a>Vea también  
 [Novedades de la API del complemento de control de código fuente, versión 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)