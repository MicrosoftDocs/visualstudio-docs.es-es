---
title: Registro de VSPackages | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc8082d63376abeab2da0e8fa7b999c12195d4e7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55006078"
---
# <a name="registering-vspackages"></a>Registro de VSPackages
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se basa en archivos .pkgdef para describir y buscar un paquete VSPackage. Un archivo .pkgdef contiene toda la información de registro en caso contrario, se agregaría al registro del sistema. Se registran los paquetes VSPackage administrados agregando atributos al código fuente y, a continuación, ejecute el [utilidad CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md) en el ensamblado resultante para generar un archivo .pkgdef.  
  
## <a name="in-this-section"></a>En esta sección  
 [Especificación de la ubicación del archivo de VSPackage en el Shell de VS](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 Describe la ruta de acceso de carga de VSPackages.  
  
 [Registrar y anulación deel registro de VSPackages](../../extensibility/registering-and-unregistering-vspackages.md)  
 Explica cómo registrar un VSPackage.  
