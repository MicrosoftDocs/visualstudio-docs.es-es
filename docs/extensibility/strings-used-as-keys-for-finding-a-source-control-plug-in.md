---
title: Cadenas utilizadas como claves para encontrar un complemento de control de código fuente Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f9333ff1b6742ca14dc5541bd15e92b2eb39085
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699717"
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>Cadenas usadas como claves para buscar un complemento de control de código fuente
Las siguientes cadenas son las claves para tener acceso al registro para encontrar información sobre el complemento de control de código fuente.

 `STR_SCC_PROVIDER_REG_LOCATION`, `STR_PROVIDERREGKEY` `STR_SCCPROVIDERPATH`, `STR_SCCPROVIDERNAME` , y son claves del Registro o valores que se usan para registrar un archivo DLL como un complemento de control de código fuente para Visual Studio.

 `SCC_PROJECTNAME_KEY`, `SCC_PROJECTAUX_KEY` `SCC_KEY, SCC_FILE_SIGNATURE`, `SCC_STATUS_FILE` , y se utilizan para describir el formato del MSSCCPRJ. SCC.

## <a name="string-keys-and-values"></a>Claves y valores de cadena

|Clave|Value|
|---------|-----------|
|`STR_SCC_PROVIDER_REG_LOCATION`|Software-SourceCodeControlProvider|
|`STR_PROVIDERREGKEY`|ProviderRegKey|
|`STR_SCCPROVIDERPATH`|SCCServerPath|
|`STR_SCCPROVIDERNAME`|SCCServerName|
|`STR_SCC_INI_SECTION`|Control de código fuente|
|`STR_SCC_INI_KEY`|SourceCodeControlProvider|
|`SCC_PROJECTNAME_KEY`|SCC_Project_Name|
|`SCC_PROJECTAUX_KEY`|SCC_Aux_Path|
|`SCC_STATUS_FILE`|MSSCCPRJ. Scc|
|`SCC_KEY`|SCC|
|`SCC_FILE_SIGNATURE`|Un archivo de control de código fuente|
|`SCC_NSE`|Extensión del espacio de nombres|
|`SCC_NSE_PREFIX`|Prefijo protocal|
|`SCC_NSE_DisableOpenSCC`|DisableOpenFromSourceControl|
|`STR_SCCHELPCOLLECTION`|HelpCollection|
|`STR_UI_LANGUAGE`|UILanguage|
|`STR_SRCSAFE_ROOT_KEY`|Software-Microsoft-SourceSafe|

## <a name="see-also"></a>Vea también
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
- [Instalación de un complemento de control de código fuente](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [Archivo MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)
