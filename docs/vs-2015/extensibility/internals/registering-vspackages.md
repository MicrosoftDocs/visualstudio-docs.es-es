---
title: Registro de VSPackages | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 053157b0ce1cb4250d8c666725431515c75b5fa2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157387"
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
