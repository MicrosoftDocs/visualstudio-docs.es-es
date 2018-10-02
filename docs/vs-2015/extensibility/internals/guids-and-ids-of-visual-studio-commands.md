---
title: GUID e identificadores de comandos de Visual Studio | Microsoft Docs
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
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bc949b400cc5c6a6efe231dff8f0ae17155ef6e1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47579555"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>GUID e identificadores de comandos de Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [GUID e identificadores de comandos de Visual Studio](https://docs.microsoft.com/visualstudio/extensibility/internals/guids-and-ids-of-visual-studio-commands).  
  
Los valores GUID y el Id. de los comandos incluidos en el entorno de desarrollo integrado (IDE) de Visual Studio se definen en archivos de vsct que se instalan como parte del SDK de Visual Studio. Para obtener más información, consulte [grupos, menús y comandos de IDE-Defined](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
 Para obtener más información sobre cómo trabajar con objetos IDE que se definen en archivos .vsct, vea [ampliación de menús y comandos](../../extensibility/extending-menus-and-commands.md).  
  
## <a name="finding-a-command-definition"></a>Buscar una definición de comando  
 Dado que Visual Studio define los comandos de más de mil, no resulta práctico para que aparezcan todas aquí. En su lugar, siga estos pasos para encontrar la definición de un comando.  
  
#### <a name="to-locate-a-command-definition"></a>Para buscar una definición de comando  
  
1.  En Visual Studio, abra los archivos siguientes en el *ruta de instalación de Visual Studio SDK*carpeta \VisualStudioIntegration\Common\Inc\: SharedCmdDef.vsct, ShellCmdDef.vsct, VsDbgCmdUsed.vsct, Venusmenu.vsct.  
  
     La mayoría de los comandos de Visual Studio se definen en SharedCmdDef.vsct y ShellCmdDef.vsct. VsDbgCmdUsed.vsct define los comandos relacionados con el depurador y Venusmenu.vsct define los comandos que son específicos para el desarrollo Web.  
  
2.  Si el comando es un elemento de menú, tenga en cuenta el texto exacto del elemento de menú. Si el comando es un botón en una barra de herramientas, tenga en cuenta el texto de información sobre herramientas que aparece cuando se coloca en él.  
  
3.  Presione CTRL + F para abrir el **buscar** cuadro de diálogo.  
  
4.  En el **buscar** , escriba el texto que anotó en el paso 2.  
  
5.  Compruebe que **todos los documentos abiertos** se muestra en el **buscar en** cuadro.  
  
6.  Haga clic en el **Buscar siguiente** botón hasta que el texto seleccionado en el `<Strings>` sección de un [elemento Button](../../extensibility/button-element.md).  
  
     El `<Button>` es de elemento que el comando aparezca en la definición de comando.  
  
 Cuando haya encontrado la definición de comando, puede colocar una copia del comando en otro menú o barra de herramientas mediante la creación de un [CommandPlacement (elemento)](../../extensibility/commandplacement-element.md) que tiene el mismo `guid` y `id` valores como el comando. Para obtener más información, consulte [creación de grupos reutilizables de botones](../../extensibility/creating-reusable-groups-of-buttons.md).  
  
### <a name="special-cases"></a>Casos especiales  
 En los casos siguientes, el texto de menú o el texto de información sobre herramientas puede no coincidir exactamente con lo que está en la definición de comando.  
  
-   Los elementos de menú que incluyen un carácter subrayado, como el **impresión** comando el **archivo** menú, en el que está subrayado la P.  
  
     Los caracteres que van precedidos por el carácter '&' en nombres de elemento de menú aparecen subrayadas. Sin embargo, los archivos .vsct se escriben en XML, que usa el carácter '&' para indicar los caracteres especiales y requiere que se debe escribir una y comercial que se muestra como&amp;'. Por lo tanto, en un archivo .vsct, el **P**comando Imprimir aparece como "&amp;impresión '.  
  
-   Los comandos que tienen texto dinámico, como **guardar** *nombre de archivo actual*y genera dinámicamente elementos de menú, como los elementos en el **archivos recientes** lista.  
  
     No hay ninguna forma confiable para realizar búsquedas de texto dinámico. En su lugar, buscar un grupo que hospeda el comando deseado consultando [GUID e identificadores de menús de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) o [GUID e identificadores de Visual Studio las barras de herramientas](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)y busque el Id. de ese grupo. Si la definición de comando no tiene el grupo como su [elemento primario](../../extensibility/parent-element.md), busque SharedCmdPlace.vsct y ShellCmdPlace.vsct (o VsDbgCmdPlace.vsct para los comandos del depurador) un `<CommandPlacement>` elemento que establece el elemento primario de la comando. AndVsDbgCmdPlace.vsct SharedCmdPlace.vsct, ShellCmdPlace.vsct, están en el *ruta de instalación del SDK de Visual Studio*\VisualStudioIntegration\Common\Inc\ carpeta.  
  
## <a name="see-also"></a>Vea también  
 [MenuCommands frente a OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md)   
 [Tabla de comandos de Visual Studio (. Archivos Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Referencia del esquema XML de VSCT](../../extensibility/vsct-xml-schema-reference.md)

