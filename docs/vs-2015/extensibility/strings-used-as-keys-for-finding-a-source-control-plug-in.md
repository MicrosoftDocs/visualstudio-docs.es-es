---
title: Las cadenas utilizadas como claves para buscar un Control de código fuente complemento | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, strings used for finding
ms.assetid: c1e31f76-42a1-4c3d-afb2-664044ef12fd
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1e2a663f11834a063faa0017cd37f6f542ab98ad
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47576621"
---
# <a name="strings-used-as-keys-for-finding-a-source-control-plug-in"></a>Cadenas usadas como claves para buscar un complemento de control de código fuente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [cadenas utilizadas como claves para buscar un complemento de Control de código fuente](https://docs.microsoft.com/visualstudio/extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in).  
  
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
|`SCC_STATUS_FILE`|MSSCCPRJ. CONTROL DE CÓDIGO FUENTE|  
|`SCC_KEY`|CONTROL DE CÓDIGO FUENTE|  
|`SCC_FILE_SIGNATURE`|Un archivo de control de código fuente|  
|`SCC_NSE`|Extensión de Namespace|  
|`SCC_NSE_PREFIX`|Prefijo de protocolo|  
|`SCC_NSE_DisableOpenSCC`|DisableOpenFromSourceControl|  
|`STR_SCCHELPCOLLECTION`|HelpCollection|  
|`STR_UI_LANGUAGE`|UILanguage|  
|`STR_SRCSAFE_ROOT_KEY`|Software\Microsoft\SourceSafe|  
  
## <a name="see-also"></a>Vea también  
 [Complementos de Control de código fuente](../extensibility/source-control-plug-ins.md)   
 [Cómo: instalar un complemento de Control de código fuente](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [Archivo MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)

