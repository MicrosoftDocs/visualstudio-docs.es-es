---
title: Modificación del Shell aislado mediante el uso de la. Archivo de Vsct | Documentos de Microsoft
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68194236"
---
# <a name="modifying-the-isolated-shell-by-using-the-vsct-file"></a>Modificación del Shell aislado mediante el uso de la. Archivo de Vsct
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El proyecto de interfaz de usuario para un proyecto de Visual Studio shell aislado contiene un archivo .vsct que le permite especificar qué comandos individuales y grupos de aplicaciones están disponibles en la aplicación. El siguiente es un extracto de un archivo .vsct sin modificar.  
  
```  
<!-- <Define name="No_WindowListCommand"/> -->  
<!-- <Define name="No_MoreWindowsCommand"/> -->  
<!-- <Define name="No_PaneNextPaneCommand"/> -->  
<!-- <Define name="No_PanePrevPaneCommand"/> -->  
```  
  
 De forma predeterminada, se incluyen la mayoría de los comandos y grupos de comandos. Para excluir un comando o un grupo de comandos, simplemente quite ese comando o un grupo.  
  
 Por ejemplo, para quitar el panel siguiente y comandos de panel anterior, quite el `No_PaneNextPaneCommand` y `No_PanePrevPaneCommand` entradas:  
  
```  
  
<Define name="No_PaneNextPaneCommand"/> <Define name="No_PanePrevPaneCommand"/>  
  
```  
  
 Para obtener más ejemplo estas personalizaciones, consulte [Tutorial: Creando un Basic aislado la aplicación de Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="referenced-files"></a>Archivos que se hace referencia  
 El archivo .vsct predeterminado para una aplicación hace referencia a los siguientes archivos. Estos archivos se encuentran en el subdirectorio \VisualStudioIntegration\Common\Inc\ del directorio de instalación del SDK de Visual Studio.  
  
|Archivo|DESCRIPCIÓN|  
|----------|-----------------|  
|wbids.h|Identidades de la interfaz de usuario para el paquete Web examinar.|  
|AppIDCmdUsed.vsct|Tabla de comandos para los elementos principales de la interfaz de usuario de Visual Studio.|  
|EmulatorCmdUsed.vsct|Tabla de comandos para elementos de interfaz de usuario de emulación de editor Emacs y breve.|  
|Vsdebugguids.h|Define los GUID de los comandos, página de opciones y otras características del depurador de Visual Studio.|  
|VsDbgCmdUsed.vsct|Tabla de comandos para el depurador.|  
  
 El archivo AppIDCmdUsed.vsct incluye elementos de interfaz de usuario de Visual Studio en función de los símbolos definidos en el archivo .vsct la aplicación.  
  
 Para obtener más información, consulte [diseño de tabla de comandos XML (. Archivos Vsct)](../extensibility/internals/designing-xml-command-table-dot-vsct-files.md) y [referencia del esquema XML de VSCT](../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="see-also"></a>Vea también  
 [Shell aislado de Visual Studio](../extensibility/visual-studio-isolated-shell.md)
