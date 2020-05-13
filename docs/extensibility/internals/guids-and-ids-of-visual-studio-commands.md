---
title: GUID e iD de los comandos de Visual Studio Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8932f23d301eabc97414bf76453d70336e0dabae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708250"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>GUID e iD de comandos de Visual Studio
Los valores GUID e ID de los comandos incluidos en el entorno de desarrollo integrado (IDE) de Visual Studio se definen en archivos .vsct que se instalan como parte del SDK de Visual Studio. Para obtener más información, consulte [Comandos, menús y grupos definidos por IDE.](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)

 Para obtener más información sobre cómo trabajar con objetos IDE definidos en archivos *.vsct,* vea [Extender menús y comandos](../../extensibility/extending-menus-and-commands.md).

## <a name="find-a-command-definition"></a>Buscar una definición de comando
 Dado que Visual Studio define más de 1000 comandos, no es práctico enumerarlos todos aquí. En su lugar, siga estos pasos para buscar la definición de un comando.

### <a name="to-locate-a-command-definition"></a>Para localizar una definición de comando

1. En Visual Studio, abra los siguientes archivos en la ruta de instalación del *SharedCmdDef.vsct*SDK de<Visual *ShellCmdDef.vsct* *VsDbgCmdUsed.vsct* *\>Studio.\\ * *Venusmenu.vsct*

    La mayoría de los comandos de Visual Studio se definen en *SharedCmdDef.vsct* y *ShellCmdDef.vsct*. *VsDbgCmdUsed.vsct* define comandos que pertenecen al depurador y *Venusmenu.vsct* define comandos que son específicos del desarrollo web.

2. Si el comando es un elemento de menú, anote el texto exacto del elemento de menú. Si el comando es un botón de una barra de herramientas, tenga en cuenta el texto de información sobre herramientas que aparece al hacer una pausa en él.

3. Presione **Ctrl**+**F** para abrir el cuadro de diálogo **Buscar.**

4. En el cuadro **Buscar,** escriba el texto que anotó en el paso 2.

5. Compruebe que **Todos los documentos abiertos** se muestra en el cuadro **Buscar en.**

6. Haga clic en el botón Buscar `<Strings>` **siguiente** hasta que el texto esté seleccionado en la sección de un elemento [Button](../../extensibility/button-element.md).

    El `<Button>` elemento en el que aparece el comando es la definición del comando.

   Cuando haya encontrado la definición de comando, puede colocar una copia del comando en otro `guid` `id` menú o barra de herramientas creando un [elemento CommandPlacement](../../extensibility/commandplacement-element.md) que tenga el mismo y los valores que el comando. Para obtener más información, consulte [Crear grupos de botones reutilizables.](../../extensibility/creating-reusable-groups-of-buttons.md)

### <a name="special-cases"></a>Casos especiales
 En los siguientes casos, es posible que el texto del menú o el texto de información sobre herramientas no coincidan exactamente con lo que hay en la definición del comando.

- Elementos de menú que incluyen un carácter subrayado, como el comando **Imprimir** del menú **Archivo,** en el que se subraya la *P.*

     Los caracteres precedidos por el carácter de y comercial (&) en los nombres de elementos de menú se muestran como subrayados. Sin embargo, los archivos *.vsct* se escriben en XML, que utiliza el carácter ampersand (&) para indicar caracteres especiales y requiere que una y como muestra se demuestre debe deletrear como * &amp;amp;*. Por lo tanto, en un archivo *.vsct,* el comando **Imprimir** aparece como * &amp;amp; Imprimir*.

- Comandos que tienen texto **Save** \<dinámico,\>como Guardar nombre de archivo actual , y elementos de menú generados dinámicamente, como los elementos de la lista **Archivos recientes.**

     No hay una forma confiable de buscar texto dinámico. En su lugar, busque un grupo que hospede el comando deseado consultando [GUID e identificadores de menús](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) o GUID de Visual Studio [e identificadores de las](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)barras de herramientas de Visual Studio y busque en el identificador de ese grupo. Si la definición de comando no tiene el grupo como su [elemento primario](../../extensibility/parent-element.md), busque *SharedCmdPlace.vsct* y *ShellCmdPlace.vsct* (o *VsDbgCmdPlace.vsct* para los comandos del depurador) para un `<CommandPlacement>` elemento que establezca el elemento primario del comando. *SharedCmdPlace.vsct*, *ShellCmdPlace.vsct*y *VsDbgCmdPlace.vsct* se encuentran en la * \<ruta\>\\ * de instalación del SDK de Visual Studio .

## <a name="see-also"></a>Vea también

- [Archivos de tabla de comandos de Visual Studio (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Referencia de esquema XML de VSCT](../../extensibility/vsct-xml-schema-reference.md)
