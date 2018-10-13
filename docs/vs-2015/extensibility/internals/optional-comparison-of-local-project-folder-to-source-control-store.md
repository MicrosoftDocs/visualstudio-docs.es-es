---
title: Comparación opcional de carpeta del proyecto Local para Store de Control de código fuente | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d904b279757e034050b79e16c1c1d61382e54746
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49276658"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Comparación opcional de la carpeta de proyecto local con el almacén de control de código fuente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Origen de controlar el complemento API 1.2 se lleva a cabo la comparación entre la carpeta del proyecto local y el control de código fuente mediante el uso de las funciones [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) y [SccDirDiff](../../extensibility/sccdirdiff-function.md).  
  
 Dentro de **el Explorador de soluciones**, si se selecciona una carpeta en lugar de un archivo individual, el **comparar versiones** invoca el nuevo menú contextual [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) y [ SccDirDiff](../../extensibility/sccdirdiff-function.md) en el complemento de control de código fuente.  
  
## <a name="new-capability-flags"></a>Marcadores de capacidad nueva  
 `SCC_CAP_DIRECTORYDIFF`  
  
 `SCC_CAP_DIRECTORYCHECKOUT`  
  
## <a name="new-functions"></a>Nuevas funciones  
 [SccDirDiff](../../extensibility/sccdirdiff-function.md)  
  
 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)  
  
 El `SccDirQueryInfo` función se llama antes de `SccDirDiff` para determinar si el directorio de trabajo controlados por código fuente. El `SccDirDiff` función muestra las diferencias entre el directorio local actual y la carpeta de control de código fuente correspondiente. Este comando solicita el control de código fuente para mostrar la lista de cambios en el directorio. Un complemento de control de código fuente proporciona su propia interfaz de usuario para mostrar las diferencias.  
  
> [!NOTE]
>  Esta función utiliza los mismos marcadores de comando como [SccDiff](../../extensibility/sccdiff-function.md). Como un proveedor de complemento de control de código fuente, puede no admitir la operación de "comparación rápida" para los directorios.  
  
## <a name="see-also"></a>Vea también  
 [Novedades de la API del complemento de control de código fuente, versión 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

