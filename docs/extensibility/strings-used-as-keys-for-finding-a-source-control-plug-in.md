---
title: Cadenas usadas como claves para buscar un complemento de control de código fuente
description: Obtenga información sobre las cadenas que son las claves para tener acceso al registro para buscar información sobre el complemento de control de código fuente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b61c13973ac6668814fbc3ba076b373d6e0b1e44
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056303"
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>Cadenas usadas como claves para buscar un complemento de control de código fuente
Las siguientes cadenas son las claves para tener acceso al registro para buscar información sobre el complemento de control de código fuente.

 `STR_SCC_PROVIDER_REG_LOCATION`, `STR_PROVIDERREGKEY` , `STR_SCCPROVIDERPATH` y `STR_SCCPROVIDERNAME` son claves del registro o valores que se usan para registrar un archivo dll como complemento de control de código fuente para Visual Studio.

 `SCC_PROJECTNAME_KEY`, `SCC_PROJECTAUX_KEY` , `SCC_KEY, SCC_FILE_SIGNATURE` y `SCC_STATUS_FILE` se usan para describir el formato de MSSCCPRJ. Archivo SCC.

## <a name="string-keys-and-values"></a>Claves y valores de cadena

|Clave|Value|
|---------|-----------|
|`STR_SCC_PROVIDER_REG_LOCATION`|Software\SourceCodeControlProvider|
|`STR_PROVIDERREGKEY`|ProviderRegKey|
|`STR_SCCPROVIDERPATH`|SCCServerPath|
|`STR_SCCPROVIDERNAME`|SCCServerName|
|`STR_SCC_INI_SECTION`|Control de código fuente|
|`STR_SCC_INI_KEY`|SourceCodeControlProvider|
|`SCC_PROJECTNAME_KEY`|SCC_Project_Name|
|`SCC_PROJECTAUX_KEY`|SCC_Aux_Path|
|`SCC_STATUS_FILE`|MSSCCPRJ. CCO|
|`SCC_KEY`|SCC|
|`SCC_FILE_SIGNATURE`|Un archivo de control de código fuente|
|`SCC_NSE`|Extensión de espacio de nombres|
|`SCC_NSE_PREFIX`|Prefijo protocolo|
|`SCC_NSE_DisableOpenSCC`|DisableOpenFromSourceControl|
|`STR_SCCHELPCOLLECTION`|HelpCollection|
|`STR_UI_LANGUAGE`|UILanguage|
|`STR_SRCSAFE_ROOT_KEY`|Software\Microsoft\SourceSafe|

## <a name="see-also"></a>Consulte también
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
- [Instalación de un complemento de control de código fuente](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [Archivo MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)
