---
title: GUID e IDs de Visual Studio comandos | Microsoft Docs
description: Obtenga información sobre cómo buscar los valores guid e identificador de los comandos incluidos en Visual Studio entorno de desarrollo integrado (IDE).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8442e6430ead8f28d2afc7f51d14968b6999fcd9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898284"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>GUID e IDs de Visual Studio comandos
Los valores guid e identificador de los comandos incluidos en el entorno de desarrollo integrado (IDE) de Visual Studio se definen en los archivos .vsct que se instalan como parte del SDK de Visual Studio. Para obtener más información, [vea Comandos, menús y grupos definidos por](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)ide.

 Para obtener más información sobre cómo trabajar con objetos IDE definidos en archivos *.vsct,* vea [Extender menús y comandos](../../extensibility/extending-menus-and-commands.md).

## <a name="find-a-command-definition"></a>Buscar una definición de comando
 Dado Visual Studio define más de 1000 comandos, no es práctico enumerarlos aquí. En su lugar, siga estos pasos para buscar la definición de un comando.

### <a name="to-locate-a-command-definition"></a>Para buscar una definición de comando

1. En Visual Studio, abra los siguientes archivos en la ruta de instalación del SDK de *<Visual Studio \> \\ \VisualStudioIntegration\Common\Inc* carpeta: *SharedCmdDef.vsct*, *ShellCmdDef.vsct*, *VsDbgCmdUsed.vsct*, *Vamenu.vsct*.

    La mayoría Visual Studio comandos se definen en *SharedCmdDef.vsct* y *ShellCmdDef.vsct*. *VsDbgCmdUsed.vsct* define comandos que pertenecen al depurador y *Xsltmenu.vsct* define comandos específicos del desarrollo web.

2. Si el comando es un elemento de menú, anote el texto exacto del elemento de menú. Si el comando es un botón de una barra de herramientas, anote el texto de información sobre herramientas que aparece al pausar en él.

3. Presione **Ctrl** + **F** para abrir el **cuadro de** diálogo Buscar.

4. En el **cuadro Buscar,** escriba el texto que anotó en el paso 2.

5. Compruebe que **todos los documentos abiertos** se muestran en el **cuadro** Buscar en .

6. Haga clic **en el botón Buscar** siguiente hasta que se seleccione el texto en la sección de un elemento `<Strings>` [Button](../../extensibility/button-element.md).

    El `<Button>` elemento en el que aparece el comando es la definición del comando.

   Cuando haya encontrado la definición de comando, puede colocar una copia del comando en otro menú o barra de herramientas mediante la creación de un elemento [CommandPlacement](../../extensibility/commandplacement-element.md) que tenga los mismos valores y que `guid` `id` el comando. Para obtener más información, vea [Crear grupos reutilizables de botones.](../../extensibility/creating-reusable-groups-of-buttons.md)

### <a name="special-cases"></a>Casos especiales
 En los casos siguientes, es posible que el texto del menú o el texto de la información sobre herramientas no coincida exactamente con lo que está en la definición del comando.

- Elementos de menú que incluyen un  carácter subrayado,  como el comando Imprimir del menú Archivo, en el que la *P* está subrayada.

     Los caracteres precedidos por el carácter de y comercial (&) en los nombres de los elementos de menú se muestran como subrayados. Sin embargo, los archivos *.vsct* se escriben en XML, que usa el carácter yand (&) para indicar caracteres especiales y requiere que una yand que se muestre se deletree como *&amp; y*. Por lo tanto, en *un archivo .vsct,* el **comando Imprimir** aparece como *&amp; y . Imprima*.

- Comandos que tienen texto dinámico, como Guardar, y elementos de menú generados dinámicamente, como los elementos de  \<Current Filename\> la lista **Archivos** recientes.

     No hay ninguna manera confiable de buscar en texto dinámico. En su lugar, busque un grupo que hospeda el comando deseado consultando GUID e identificadores de [menús](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) de Visual Studio o GUID e identificadores de barras de herramientas de [Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)y busque el identificador de ese grupo. Si la definición del comando no tiene el grupo como elemento [Parent](../../extensibility/parent-element.md), busque *SharedCmdPlace.vsct* y *ShellCmdPlace.vsct* (o *VsDbgCmdPlace.vsct* para los comandos del depurador) para un elemento que establece el elemento primario del `<CommandPlacement>` comando. *SharedCmdPlace.vsct,* *ShellCmdPlace.vsct* y *VsDbgCmdPlace.vsct* se encuentran en la carpeta *\<Visual Studio SDK installation path\> \VisualStudioIntegration\Common\Inc. \\*

## <a name="see-also"></a>Consulta también

- [Visual Studio de tabla de comandos (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Referencia de esquema XML de VSCT](../../extensibility/vsct-xml-schema-reference.md)
