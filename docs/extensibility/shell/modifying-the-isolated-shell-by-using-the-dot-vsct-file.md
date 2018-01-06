---
title: Modificar el Shell aislado mediante el. Archivo de Vsct | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode, .vsct file
ms.assetid: 6d147c2d-10e9-400e-b8ce-5566287b41ba
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 631aaaf4bf3d36cf5b83c8e67791c453cdfed925
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="modifying-the-isolated-shell-by-using-the-vsct-file"></a>Modificar el Shell aislado mediante el. Archivo de Vsct
El proyecto de la interfaz de usuario para un proyecto de shell aislado de Visual Studio contiene un archivo .vsct que le permite especificar qué grupos de aplicaciones y los comandos individuales están disponibles en la aplicación. El siguiente es un extracto de un archivo .vsct sin modificar.  
  
```  
<!-- <Define name="No_WindowListCommand"/> -->  
<!-- <Define name="No_MoreWindowsCommand"/> -->  
<!-- <Define name="No_PaneNextPaneCommand"/> -->  
<!-- <Define name="No_PanePrevPaneCommand"/> -->  
```  
  
 De forma predeterminada, se incluyen la mayoría de los comandos y grupos de comandos. Para excluir un comando o un grupo de comandos, simplemente quite ese comando o el grupo.  
  
 Por ejemplo, para quitar el panel siguiente y comandos de panel anterior, quite el `No_PaneNextPaneCommand` y `No_PanePrevPaneCommand` entradas:  
  
```  
  
<Define name="No_PaneNextPaneCommand"/> <Define name="No_PanePrevPaneCommand"/>  
  
```  
  
 Para más obtener ejemplo estas personalizaciones, consulte [Tutorial: crear una aplicación de Shell aislado básica](walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="referenced-files"></a>Archivos que se hace referencia  
 El archivo de vsct predeterminado para una aplicación hace referencia a los siguientes archivos. Estos archivos se encuentran en el subdirectorio \VisualStudioIntegration\Common\Inc\ del directorio de instalación de SDK de Visual Studio.  
  
|Archivo|Descripción|  
|----------|-----------------|  
|wbids.h|Identidades de interfaz de usuario para el paquete Web examinar.|  
|AppIDCmdUsed.vsct|Tabla de comandos para los principales elementos de interfaz de usuario de Visual Studio.|  
|EmulatorCmdUsed.vsct|Tabla de comandos para los elementos de interfaz de usuario de emulación de editor Emacs y breve.|  
|Vsdebugguids.h|Define los GUID de los comandos, página de opciones y otras características del depurador de Visual Studio.|  
|VsDbgCmdUsed.vsct|Tabla de comandos para el depurador.|  
  
 El archivo AppIDCmdUsed.vsct incluye elementos de interfaz de usuario de Visual Studio en función de los símbolos definidos en el archivo .vsct de aplicación.  
  
 Para obtener más información, vea [diseñar la tabla de comandos de XML (. Archivos Vsct)](../internals/designing-xml-command-table-dot-vsct-files.md) y [referencia del esquema XML de VSCT](../vsct-xml-schema-reference.md).  
  
## <a name="see-also"></a>Vea también  
 [Shell aislado de Visual Studio](visual-studio-isolated-shell.md)