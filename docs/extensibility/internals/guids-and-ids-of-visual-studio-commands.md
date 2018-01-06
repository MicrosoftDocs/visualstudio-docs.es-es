---
title: GUID e identificadores de comandos de Visual Studio | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 44ae5ff7e9095d6c88d753342da30983b30b7364
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>GUID e identificadores de comandos de Visual Studio
Los valores GUID y el ID de los comandos incluidos en el entorno de desarrollo integrado (IDE) de Visual Studio se definen en archivos de vsct que se instalan como parte del SDK de Visual Studio. Para obtener más información, consulte [IDE-Defined comandos, menús y grupos](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
 Para obtener más información sobre cómo trabajar con objetos IDE que se definen en archivos de vsct, consulte [extender menús y comandos de](../../extensibility/extending-menus-and-commands.md).  
  
## <a name="finding-a-command-definition"></a>Buscar una definición de comando  
 Dado que Visual Studio define los comandos de más de mil, no resulta práctico para enumerarlos aquí todos. En su lugar, siga estos pasos para encontrar la definición de un comando.  
  
#### <a name="to-locate-a-command-definition"></a>Para buscar una definición de comando  
  
1.  En Visual Studio, abra los archivos siguientes en la *ruta de instalación del SDK de Visual Studio*\VisualStudioIntegration\Common\Inc\ carpeta: SharedCmdDef.vsct, ShellCmdDef.vsct, VsDbgCmdUsed.vsct, Venusmenu.vsct.  
  
     La mayoría de los comandos de Visual Studio se definen en SharedCmdDef.vsct y ShellCmdDef.vsct. VsDbgCmdUsed.vsct define los comandos que pertenecen al depurador y Venusmenu.vsct define los comandos que son específicos del desarrollo Web.  
  
2.  Si el comando es un elemento de menú, tenga en cuenta el texto exacto del elemento de menú. Si el comando es un botón en una barra de herramientas, tenga en cuenta el texto de información sobre herramientas que aparece cuando se coloca en él.  
  
3.  Presione CTRL + F para abrir el **buscar** cuadro de diálogo.  
  
4.  En el **buscar** , escriba el texto que anotó en el paso 2.  
  
5.  Compruebe que **todos los documentos abiertos** se muestra en el **buscar en** cuadro.  
  
6.  Haga clic en el **Buscar siguiente** botón hasta que el texto seleccionado en el `<Strings>` sección de un [elemento Button](../../extensibility/button-element.md).  
  
     El `<Button>` es de elemento que el comando aparece en la definición de comando.  
  
 Cuando haya encontrado la definición de comando, puede colocar una copia del comando en otro menú o barra de herramientas mediante la creación de un [CommandPlacement elemento](../../extensibility/commandplacement-element.md) que tiene el mismo `guid` y `id` valores como el comando. Para obtener más información, consulte [crear grupos de reutilizable de botones](../../extensibility/creating-reusable-groups-of-buttons.md).  
  
### <a name="special-cases"></a>Casos especiales  
 En los casos siguientes, el texto de menú o el texto de información sobre herramientas puede no coincidir exactamente con lo que aparece en la definición de comando.  
  
-   Elementos de menú que incluyen un carácter de subrayado, como el **impresión** comando el **archivo** menú, en el que está subrayada la P.  
  
     Los caracteres que estén precedidos por el carácter '&' en nombres de elemento de menú se muestran como subrayado. Sin embargo, los archivos .vsct se escriben en XML, que utiliza el carácter '&' para indicar los caracteres especiales y requiere que se debe escribir una y comercial que se muestra como&amp;'. Por lo tanto, en un archivo .vsct, el **P**rint comando aparece como '&amp;impresión '.  
  
-   Los comandos que tienen texto dinámico, como **guardar** *nombre de archivo actual*y genera dinámicamente los elementos de menú, como los elementos en el **archivos recientes** lista.  
  
     No hay ninguna forma confiable para realizar búsquedas de texto dinámico. En su lugar, encuentre el grupo que hospeda el comando deseado consultando [GUID e identificadores de menús de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) o [GUID e identificadores de Visual Studio barras de herramientas](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)y busque el identificador de ese grupo. Si la definición de comando no tiene el grupo como su [elemento primario](../../extensibility/parent-element.md), busque SharedCmdPlace.vsct y ShellCmdPlace.vsct (o VsDbgCmdPlace.vsct para comandos del depurador) un `<CommandPlacement>` elemento que establece el elemento primario de la comando. AndVsDbgCmdPlace.vsct SharedCmdPlace.vsct, ShellCmdPlace.vsct, están en el *ruta de instalación del SDK de Visual Studio*\VisualStudioIntegration\Common\Inc\ carpeta.  
  
## <a name="see-also"></a>Vea también  
 [MenuCommands frente a OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)   
 [Tabla de comandos de Visual Studio (. Archivos Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Referencia del esquema XML de VSCT](../../extensibility/vsct-xml-schema-reference.md)