---
title: Registro de VSPackages | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 119e6dc088c6f6e80d79ab096d97b7404c530611
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="registering-vspackages"></a>Registro de VSPackages
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]se basa en los archivos de .pkgdef para describir y buscar un VSPackage. Un archivo .pkgdef contiene toda la información de registro en caso contrario, se debe agregar al registro del sistema. VSPackages administrado se registran agregando atributos al código fuente y, a continuación, ejecuta el [CreatePkgDef utilidad](../../extensibility/internals/createpkgdef-utility.md) en el ensamblado resultante para generar un archivo .pkgdef.  
  
## <a name="in-this-section"></a>En esta sección  
 [Especificación de la ubicación del archivo de VSPackage en el Shell de VS](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 Describe la ruta de acceso de carga de VSPackages.  
  
 [Registrar y anulación deel registro de VSPackages](../../extensibility/registering-and-unregistering-vspackages.md)  
 Explica cómo registrar un VSPackage.  
