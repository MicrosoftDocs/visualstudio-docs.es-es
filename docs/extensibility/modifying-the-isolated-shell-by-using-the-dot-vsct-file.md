---
title: Modificar el Shell aislado mediante el. Archivo de Vsct | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode, .vsct file
ms.assetid: 6d147c2d-10e9-400e-b8ce-5566287b41ba
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: a20b546c6e8d6d70a17d3d0bae575a5b2898d781
ms.lasthandoff: 02/22/2017

---
# <a name="modifying-the-isolated-shell-by-using-the-vsct-file"></a>Modificar el Shell aislado mediante el. Archivo de Vsct
El proyecto de la interfaz de usuario para un proyecto de Visual Studio shell aislado contiene un archivo de vsct que le permite especificar qué grupos de aplicaciones y los comandos individuales están disponibles en la aplicación. El siguiente es un extracto de un archivo de vsct sin modificar.  
  
```  
<!-- <Define name="No_WindowListCommand"/> -->  
<!-- <Define name="No_MoreWindowsCommand"/> -->  
<!-- <Define name="No_PaneNextPaneCommand"/> -->  
<!-- <Define name="No_PanePrevPaneCommand"/> -->  
```  
  
 De forma predeterminada, se incluyen la mayoría de los comandos y grupos de comandos. Para excluir un comando o un grupo de comandos, simplemente quite ese comando o el grupo.  
  
 Por ejemplo, para quitar el siguiente panel y los comandos de panel anterior, quite el `No_PaneNextPaneCommand` y `No_PanePrevPaneCommand` entradas:  
  
```  
  
<Define name="No_PaneNextPaneCommand"/> <Define name="No_PanePrevPaneCommand"/>  
  
```  
  
 Para más obtener ejemplo estas personalizaciones, consulte [Tutorial: crear una aplicación básica de Shell aislado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="referenced-files"></a>Archivos de referencia  
 El archivo de vsct predeterminado para una aplicación hace referencia a los siguientes archivos. Estos archivos se encuentran en el subdirectorio \VisualStudioIntegration\Common\Inc\ del directorio de instalación del SDK de Visual Studio.  
  
|Archivo|Descripción|  
|----------|-----------------|  
|wbids.h|Identidades de interfaz de usuario para el paquete Web examinar.|  
|AppIDCmdUsed.vsct|Tabla de comandos para elementos de interfaz de usuario de Visual Studio principales.|  
|EmulatorCmdUsed.vsct|Tabla de comandos para elementos de interfaz de usuario de emulación de editor Emacs y breve.|  
|Vsdebugguids.h|Define los GUID de los comandos, página de opciones y otras características del depurador de Visual Studio.|  
|VsDbgCmdUsed.vsct|Tabla de comandos para el depurador.|  
  
 El archivo AppIDCmdUsed.vsct incluye elementos de interfaz de usuario de Visual Studio en función de los símbolos definidos en el archivo .vsct de aplicación.  
  
 Para obtener más información, consulte [diseño de tabla de comandos XML (. Archivos de Vsct)](../extensibility/internals/designing-xml-command-table-dot-vsct-files.md) y [referencia del esquema XML de VSCT](../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="see-also"></a>Vea también  
 [Shell de aislado de Visual Studio](../extensibility/visual-studio-isolated-shell.md)
