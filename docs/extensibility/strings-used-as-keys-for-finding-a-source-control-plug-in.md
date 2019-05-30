---
title: Las cadenas utilizadas como claves para buscar un Control de código fuente complemento | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31c2b30fb41976cdbbab13fa22d438c63bddbbef
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331713"
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>Cadenas usadas como claves para buscar un complemento de control de código fuente
Las siguientes cadenas son las claves de acceso al registro para obtener información sobre el control de código fuente complemento.

 `STR_SCC_PROVIDER_REG_LOCATION`, `STR_PROVIDERREGKEY`, `STR_SCCPROVIDERPATH`, y `STR_SCCPROVIDERNAME` son valores que se usa para registrar un archivo DLL como un complemento de control de código fuente para Visual Studio o las claves del registro.

 `SCC_PROJECTNAME_KEY`, `SCC_PROJECTAUX_KEY`, `SCC_KEY, SCC_FILE_SIGNATURE`, y `SCC_STATUS_FILE` se utilizan para describir el formato de la MSSCCPRJ. Archivo de control de código fuente.

## <a name="string-keys-and-values"></a>Claves de cadena y valores

|Key|Valor|
|---------|-----------|
|`STR_SCC_PROVIDER_REG_LOCATION`|Software\SourceCodeControlProvider|
|`STR_PROVIDERREGKEY`|ProviderRegKey|
|`STR_SCCPROVIDERPATH`|SCCServerPath|
|`STR_SCCPROVIDERNAME`|SCCServerName|
|`STR_SCC_INI_SECTION`|Control de código fuente|
|`STR_SCC_INI_KEY`|SourceCodeControlProvider|
|`SCC_PROJECTNAME_KEY`|SCC_Project_Name|
|`SCC_PROJECTAUX_KEY`|SCC_Aux_Path|
|`SCC_STATUS_FILE`|MSSCCPRJ.SCC|
|`SCC_KEY`|SCC|
|`SCC_FILE_SIGNATURE`|Un archivo de control de código fuente|
|`SCC_NSE`|Extensión de Namespace|
|`SCC_NSE_PREFIX`|Prefijo de protocolo|
|`SCC_NSE_DisableOpenSCC`|DisableOpenFromSourceControl|
|`STR_SCCHELPCOLLECTION`|HelpCollection|
|`STR_UI_LANGUAGE`|UILanguage|
|`STR_SRCSAFE_ROOT_KEY`|Software\Microsoft\SourceSafe|

## <a name="see-also"></a>Vea también
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
- [Cómo: Instalar un complemento de control de código fuente](../extensibility/internals/how-to-install-a-source-control-plug-in.md)
- [Archivo MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)