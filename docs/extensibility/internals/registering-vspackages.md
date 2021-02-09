---
title: Registrar VSPackages | Microsoft Docs
description: Un archivo. pkgdef contiene información que, de lo contrario, se agregaría al registro del sistema. Obtenga información sobre cómo Visual Studio usa los archivos. pkgdef para describir o localizar un VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 111debccd1623901790c83e743469327ffdd667e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905834"
---
# <a name="registering-vspackages"></a>Registro de VSPackages
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se basa en los archivos. pkgdef para describir y buscar un VSPackage. Un archivo. pkgdef contiene toda la información de registro que, de lo contrario, se agregaría al registro del sistema. Los VSPackages administrados se registran agregando atributos al código fuente y, a continuación, ejecutando la [utilidad CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md) en el ensamblado resultante para generar un archivo. pkgdef.

## <a name="in-this-section"></a>En esta sección
- [Especificación de la ubicación del archivo de VSPackage en el Shell de VS](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)

 Describe la ruta de acceso de carga para VSPackages.

- [Registrar y anulación deel registro de VSPackages](../../extensibility/registering-and-unregistering-vspackages.md)

 Explica cómo registrar un VSPackage.
