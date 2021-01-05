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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ae4d7ae70766b7e0d2d8eedb5d79d97159839146
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875120"
---
# <a name="registering-vspackages"></a>Registro de VSPackages
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se basa en los archivos. pkgdef para describir y buscar un VSPackage. Un archivo. pkgdef contiene toda la información de registro que, de lo contrario, se agregaría al registro del sistema. Los VSPackages administrados se registran agregando atributos al código fuente y, a continuación, ejecutando la [utilidad CreatePkgDef](../../extensibility/internals/createpkgdef-utility.md) en el ensamblado resultante para generar un archivo. pkgdef.

## <a name="in-this-section"></a>En esta sección
- [Especificación de la ubicación del archivo de VSPackage en el Shell de VS](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)

 Describe la ruta de acceso de carga para VSPackages.

- [Registrar y anulación deel registro de VSPackages](../../extensibility/registering-and-unregistering-vspackages.md)

 Explica cómo registrar un VSPackage.
