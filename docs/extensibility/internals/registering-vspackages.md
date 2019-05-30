---
title: Registro de VSPackages | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1ac51f23132d855c3da921cc2743c3064a353524
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331315"
---
# <a name="registering-vspackages"></a>Registro de VSPackages
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se basa en archivos .pkgdef para describir y buscar un paquete VSPackage. Un archivo .pkgdef contiene toda la información de registro en caso contrario, se agregaría al registro del sistema. Se registran los paquetes VSPackage administrados agregando atributos al código fuente y, a continuación, ejecute el [utilidad CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md) en el ensamblado resultante para generar un archivo .pkgdef.

## <a name="in-this-section"></a>En esta sección
- [Especificación de la ubicación del archivo de VSPackage en el Shell de VS](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)

 Describe la ruta de acceso de carga de VSPackages.

- [Registrar y anulación deel registro de VSPackages](../../extensibility/registering-and-unregistering-vspackages.md)

 Explica cómo registrar un VSPackage.
