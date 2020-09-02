---
title: Agregar iconos a comandos de menú | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- icons [Visual Studio], adding to toolbars
- toolbars [Visual Studio], adding icons to commands
- commands [Visual Studio], adding icons
ms.assetid: 362a0c7e-5729-4297-a83f-1aba1a37fd44
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c9f038dc43c1705a7cef47eb09a17607c535e307
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85903437"
---
# <a name="add-icons-to-menu-commands"></a>Agregar iconos a comandos de menú
Los comandos pueden aparecer en los menús y las barras de herramientas. En las barras de herramientas, es habitual que se muestre un comando con solo un icono (para ahorrar espacio) mientras que en los menús aparece normalmente un comando con un icono y texto.

 Los iconos tienen 16 píxeles de ancho por 16 píxeles de alto y pueden ser una profundidad de color de 8 bits (256 colores) o una profundidad de color de 32 bits (color verdadero). se prefieren los iconos de color de 32 bits. Normalmente, los iconos se organizan en una sola fila horizontal en un único mapa de bits, aunque se permiten varios mapas de bits. Este mapa de bits se declara en el archivo *. Vsct* junto con los iconos individuales disponibles en el mapa de bits. Vea la referencia del [elemento bitmaps](../extensibility/bitmaps-element.md) para obtener más detalles.

## <a name="add-an-icon-to-a-command"></a>Agregar un icono a un comando
 En el procedimiento siguiente se supone que tiene un proyecto de VSPackage existente con un comando de menú. Para averiguar cómo hacerlo, vea [crear una extensión con un comando de menú](../extensibility/creating-an-extension-with-a-menu-command.md).

1. Cree un mapa de bits con una profundidad de color de 32 bits. Un icono siempre es 16 x 16, por lo que este mapa de bits debe tener 16 píxeles de alto y un múltiplo de 16 píxeles de ancho.

     Cada icono se coloca en el mapa de bits junto entre sí en una sola fila. Use el canal alfa para indicar lugares de transparencia en cada icono.

     Si usa una profundidad de color de 8 bits, use magenta, `RGB(255,0,255)` , como transparencia. Sin embargo, se prefieren los iconos de color de 32 bits.

2. Copie el archivo de icono en el directorio de *recursos* del proyecto de VSPackage. En el **Explorador de soluciones**, agregue el icono al proyecto. (Seleccione **recursos**y, en el menú contextual, haga clic en **Agregar**, en **elemento existente**y seleccione el archivo de icono).

3. Abra el archivo *. Vsct* en el editor.

4. Agregue un `GuidSymbol` elemento con el nombre **testIcon**. Cree un GUID (**herramientas**  >  **crear GUID**, seleccione el **formato del registro** y haga clic en **copiar**) y péguelo en el `value` atributo. El resultado debería ser similar al siguiente:

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
    ```

5. Agregue un `<IDSymbol>` para el icono. El `name` atributo es el identificador del icono y `value` indica su posición en la franja, si existe. Si solo hay un icono, agregue 1. El resultado debería ser similar al siguiente:

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
        <IDSymbol name="testIcon1" value="1" />
    </GuidSymbol>
    ```

6. Cree un `<Bitmap>` en la `<Bitmaps>` sección del archivo *. Vsct* para representar el mapa de bits que contiene los iconos.

    - Establezca el `guid` valor en el nombre del `<GuidSymbol>` elemento que creó en el paso anterior.

    - Establezca el `href` valor en la ruta de acceso relativa del archivo de mapa de bits (en este caso, **recursos \\<\> nombre de archivo de icono**.

    - Establezca el `usedList` valor en el IDSymbol que creó anteriormente. Este atributo especifica una lista delimitada por comas de los iconos que se van a usar en el VSPackage. Los iconos que no están en la lista son la compilación de formularios excluidos.

         El bloque de mapa de bits debe tener el siguiente aspecto:

        ```xml
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>
        ```

7. En el `<Button>` elemento existente, establezca el `Icon` elemento en los valores GUIDSymbol y IDSymbol que creó anteriormente. A continuación se muestra un ejemplo de un elemento Button con estos valores:

    ```xml
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />
        <Icon guid="testIcon" id="testIcon1" />
        <Strings>
            <ButtonText>My Command name</ButtonText>
        </Strings>
    </Button>
    ```

8. Pruebe el icono. Compile la solución y comience la depuración. En la instancia experimental, busque el comando. Debería mostrar el icono que ha agregado.

## <a name="see-also"></a>Consulte también
- [Extensión de menús y comandos](../extensibility/extending-menus-and-commands.md)
- [Referencia del esquema XML de VSCT](../extensibility/vsct-xml-schema-reference.md)
