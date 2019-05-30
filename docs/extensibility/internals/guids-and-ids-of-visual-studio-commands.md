---
title: GUID e identificadores de comandos de Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89274600d05b787182ac447902555f7d703851c2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66329186"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>Comandos de GUID e identificadores de Visual Studio
Los valores GUID y el Id. de los comandos incluidos en el entorno de desarrollo integrado (IDE) de Visual Studio se definen en archivos de vsct que se instalan como parte del SDK de Visual Studio. Para obtener más información, consulte [grupos, menús y comandos definidos por el IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

 Para obtener más información sobre cómo trabajar con objetos IDE que se definen en *.vsct* archivos, consulte [amplían los menús y comandos](../../extensibility/extending-menus-and-commands.md).

## <a name="find-a-command-definition"></a>Buscar una definición de comando
 Dado que Visual Studio se define más de 1000 comandos, no resulta práctico para que aparezcan todas aquí. En su lugar, siga estos pasos para encontrar la definición de un comando.

### <a name="to-locate-a-command-definition"></a>Para buscar una definición de comando

1. En Visual Studio, abra los archivos siguientes en el *< ruta de instalación del SDK de Visual Studio\>\VisualStudioIntegration\Common\Inc\\*  carpeta: *SharedCmdDef.vsct*, *ShellCmdDef.vsct*, *VsDbgCmdUsed.vsct*, *Venusmenu.vsct*.

    La mayoría de los comandos de Visual Studio se definen en *SharedCmdDef.vsct* y *ShellCmdDef.vsct*. *VsDbgCmdUsed.vsct* define los comandos relacionados con el depurador, y *Venusmenu.vsct* define los comandos que son específicos para el desarrollo Web.

2. Si el comando es un elemento de menú, tenga en cuenta el texto exacto del elemento de menú. Si el comando es un botón en una barra de herramientas, tenga en cuenta el texto de información sobre herramientas que aparece cuando se coloca en él.

3. Presione **Ctrl**+**F** para abrir el **buscar** cuadro de diálogo.

4. En el **buscar** , escriba el texto que anotó en el paso 2.

5. Compruebe que **todos los documentos abiertos** se muestra en el **buscar en** cuadro.

6. Haga clic en el **Buscar siguiente** botón hasta que el texto seleccionado en el `<Strings>` sección de un [elemento Button](../../extensibility/button-element.md).

    El `<Button>` es de elemento que el comando aparezca en la definición de comando.

   Cuando haya encontrado la definición de comando, puede colocar una copia del comando en otro menú o barra de herramientas mediante la creación de un [CommandPlacement (elemento)](../../extensibility/commandplacement-element.md) que tiene el mismo `guid` y `id` valores como el comando. Para obtener más información, consulte [crear grupos reutilizables de botones](../../extensibility/creating-reusable-groups-of-buttons.md).

### <a name="special-cases"></a>Casos especiales
 En los casos siguientes, el texto de menú o el texto de información sobre herramientas puede no coincidir exactamente con lo que está en la definición de comando.

- Los elementos de menú que incluyen un carácter subrayado, como el **impresión** comando el **archivo** menú, en el que el *P* está subrayada.

     Carácter en los nombres de elemento de menú de caracteres que van precedidos por la y comercial (&) se muestran como subrayado. Sin embargo, *.vsct* archivos se escriben en XML, que usa el carácter de y comercial (&) para indicar los caracteres especiales y requiere que se debe escribir una y comercial que se mostrará como  *&amp;amp;* . Por lo tanto, en un *.vsct* archivo, el **impresión** comando aparece como  *&amp;amp; Impresión*.

- Los comandos que tienen texto dinámico, como **guardar** \<nombre de archivo actual\>y genera dinámicamente elementos de menú, como los elementos en el **archivos recientes** lista.

     No hay ninguna forma confiable para realizar búsquedas de texto dinámico. En su lugar, buscar un grupo que hospeda el comando deseado consultando [menús GUID e identificadores de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) o [las barras de herramientas de GUID e identificadores de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)y busque el Id. de ese grupo. Si la definición de comando no tiene el grupo como su [elemento primario](../../extensibility/parent-element.md), búsqueda *SharedCmdPlace.vsct* y *ShellCmdPlace.vsct* (o  *VsDbgCmdPlace.vsct* para los comandos del depurador) para un `<CommandPlacement>` elemento que establece el elemento primario del comando. *SharedCmdPlace.vsct*, *ShellCmdPlace.vsct*, y *VsDbgCmdPlace.vsct* están en el *\<ruta de instalación de Visual Studio SDK\>\ VisualStudioIntegration\Common\Inc\\* carpeta.

## <a name="see-also"></a>Vea también
- [MenuCommands frente a OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)
- [Archivos visuales Studio comando table (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Referencia del esquema XML de VSCT](../../extensibility/vsct-xml-schema-reference.md)
