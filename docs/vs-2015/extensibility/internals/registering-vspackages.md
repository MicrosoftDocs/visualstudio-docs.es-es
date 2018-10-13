---
title: Registro de VSPackages | Documentos de Microsoft
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
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6bbfc837323ddb103405ab289e89322ddb344040
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49243573"
---
# <a name="registering-vspackages"></a>Registro de VSPackages
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] se basa en archivos .pkgdef para describir y buscar un paquete VSPackage. Un archivo .pkgdef contiene toda la información de registro en caso contrario, se agregaría al registro del sistema. Se registran los paquetes VSPackage administrados agregando atributos al código fuente y, a continuación, ejecute el [utilidad CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md) en el ensamblado resultante para generar un archivo .pkgdef.  
  
## <a name="in-this-section"></a>En esta sección  
 [Especificación de la ubicación del archivo de VSPackage en el Shell de VS](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 Describe la ruta de acceso de carga de VSPackages.  
  
 [Registrar y anulación deel registro de VSPackages](../../extensibility/registering-and-unregistering-vspackages.md)  
 Explica cómo registrar un VSPackage.  
  
 [Usar un atributo de registro personalizado para registrar una extensión](../../misc/using-a-custom-registration-attribute-to-register-an-extension.md)  
 Describe cómo crear un manifiesto de registro que se puede usar para implementar un VSPackage administrado.

