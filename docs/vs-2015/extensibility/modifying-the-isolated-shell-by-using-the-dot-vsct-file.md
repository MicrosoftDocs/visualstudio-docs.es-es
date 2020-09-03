---
title: Modificación del shell aislado mediante el. Archivo Vsct | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .vsct file
ms.assetid: 6d147c2d-10e9-400e-b8ce-5566287b41ba
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8c106a04e809e772ac3b8a77192fb2f101161e9c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194236"
---
# <a name="modifying-the-isolated-shell-by-using-the-vsct-file"></a>Modificación del Shell aislado mediante el archivo .Vsct
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El proyecto de interfaz de usuario para un proyecto de Shell aislado de Visual Studio contiene un archivo. Vsct que le permite especificar qué grupos de aplicaciones y comandos individuales están disponibles en la aplicación. El siguiente es un extracto de un archivo. Vsct sin modificar.  
  
```  
<!-- <Define name="No_WindowListCommand"/> -->  
<!-- <Define name="No_MoreWindowsCommand"/> -->  
<!-- <Define name="No_PaneNextPaneCommand"/> -->  
<!-- <Define name="No_PanePrevPaneCommand"/> -->  
```  
  
 De forma predeterminada, se incluyen la mayoría de los comandos y los grupos de comandos. Para excluir un comando o un grupo de comandos, simplemente quite el comentario de ese comando o grupo.  
  
 Por ejemplo, para quitar los comandos panel siguiente y panel anterior, quite los comentarios de las `No_PaneNextPaneCommand` `No_PanePrevPaneCommand` entradas y:  
  
```  
  
<Define name="No_PaneNextPaneCommand"/> <Define name="No_PanePrevPaneCommand"/>  
  
```  
  
 Para obtener un ejemplo más detallado de estas personalizaciones, consulte [Tutorial: crear una aplicación básica de Shell aislado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="referenced-files"></a>Archivos a los que se hace referencia  
 El archivo. Vsct predeterminado para una aplicación hace referencia a los archivos siguientes. Estos archivos se encuentran en el subdirectorio \VisualStudioIntegration\Common\Inc\ del directorio de instalación del SDK de Visual Studio.  
  
|Archivo|Descripción|  
|----------|-----------------|  
|wbids. h|Identidades de interfaz de usuario para el paquete de exploración Web.|  
|AppIDCmdUsed. Vsct|Tabla de comandos para elementos primarios de la interfaz de usuario de Visual Studio.|  
|EmulatorCmdUsed. Vsct|Tabla de comandos para los elementos de interfaz de usuario de emulación de editor Emacs y Brief.|  
|Vsdebugguids. h|Define los GUID de los comandos, la página Opciones y otras características del depurador de Visual Studio.|  
|VsDbgCmdUsed. Vsct|Tabla de comandos para el depurador.|  
  
 El archivo AppIDCmdUsed. Vsct incluye elementos de la interfaz de usuario de Visual Studio basados en los símbolos definidos en el archivo Application. Vsct.  
  
 Para obtener más información, vea [diseñar una tabla de comandos XML (. Vsct)](../extensibility/internals/designing-xml-command-table-dot-vsct-files.md) y la [referencia de esquema XML de Vsct](../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="see-also"></a>Consulte también  
 [Shell aislado de Visual Studio](../extensibility/visual-studio-isolated-shell.md)
