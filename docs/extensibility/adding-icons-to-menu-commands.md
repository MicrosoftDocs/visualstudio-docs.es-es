---
title: Adición de iconos a los comandos de menú ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: f4b71f981472451766f526cf62e975e571cf46da
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740157"
---
# <a name="add-icons-to-menu-commands"></a>Añadir iconos a los comandos del menú
Los comandos pueden aparecer tanto en los menús como en las barras de herramientas. En las barras de herramientas, es común que un comando se muestre con solo un icono (para ahorrar espacio) mientras que en los menús suele aparecer un comando con un icono y texto.

 Los iconos tienen 16 píxeles de ancho por 16 píxeles de alto y pueden tener una profundidad de color de 8 bits (256 colores) o una profundidad de color de 32 bits (color verdadero). Se prefieren los iconos de color de 32 bits. Los iconos normalmente se organizan en una sola fila horizontal en un único mapa de bits, aunque se permiten varios mapas de bits. Este mapa de bits se declara en el archivo *.vsct* junto con los iconos individuales disponibles en el mapa de bits. Consulte la referencia del [elemento Bitmaps](../extensibility/bitmaps-element.md) para obtener más detalles.

## <a name="add-an-icon-to-a-command"></a>Añadir un icono a un comando
 En el procedimiento siguiente se supone que tiene un proyecto de VSPackage existente con un comando de menú. Para saber cómo hacerlo, consulte [Crear una extensión con un comando](../extensibility/creating-an-extension-with-a-menu-command.md)de menú .

1. Cree un mapa de bits con una profundidad de color de 32 bits. Un icono siempre es de 16 x 16, por lo que este mapa de bits debe tener 16 píxeles de alto y un múltiplo de 16 píxeles de ancho.

     Cada icono se coloca en el mapa de bits uno al lado del otro en una sola fila. Utilice el canal alfa para indicar los lugares de transparencia en cada icono.

     Si utiliza una profundidad de color de 8 `RGB(255,0,255)`bits, utilice magenta, , como transparencia. Sin embargo, se prefieren los iconos de color de 32 bits.

2. Copie el archivo de icono en el directorio *Resources* del proyecto DE VSPackage. En el Explorador de **soluciones**, agregue el icono al proyecto. (Seleccione **Recursos**y, en el menú contextual, haga clic en **Agregar**, luego en **Elemento existente**y seleccione el archivo de icono.)

3. Abra el archivo *.vsct* en el editor.

4. Agregue `GuidSymbol` un elemento con el nombre **testIcon**. Cree un GUID (**Tools** > **Create GUID**y, a continuación, seleccione Registry Format **(Formato del Registro)** y haga clic en Copy **(Copiar)** y péguelo en el `value` atributo. El resultado debería tener este aspecto:

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
    ```

5. Agregue `<IDSymbol>` un para el icono. El `name` atributo es el identificador del `value` icono y indica su posición en la tira, si existe. Si solo hay un icono, agregue 1. El resultado debería tener este aspecto:

    ```xml
    <!-- Create your own GUID -->
    <GuidSymbol name="testIcon" value="{00000000-0000-0000-0000-0000}">
        <IDSymbol name="testIcon1" value="1" />
    </GuidSymbol>
    ```

6. Cree `<Bitmap>` un `<Bitmaps>` en la sección del archivo *.vsct* para representar el mapa de bits que contiene los iconos.

    - Establezca `guid` el valor en `<GuidSymbol>` el nombre del elemento que creó en el paso anterior.

    - Establezca `href` el valor en la ruta de acceso relativa del archivo de mapa de bits (en este caso **Recursos\\<nombre\>** de archivo de icono .

    - Establezca `usedList` el valor en el IDSymbol que creó anteriormente. Este atributo especifica una lista delimitada por comas de los iconos que se usarán en el VSPackage. Los iconos que no están en la lista se excluyen la compilación de formularios.

         El bloque Bitmap debería tener este aspecto:

        ```xml
        <Bitmap guid="testIcon" href="Resources\<icon file name>" usedList="testIcon1"/>
        ```

7. En el `<Button>` elemento existente, establezca el `Icon` elemento en los valores GUIDSymbol e IDSymbol que creó anteriormente. Este es un ejemplo de un elemento Button con esos valores:

    ```xml
    <Button guid="guidAddIconCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
        <Parent guid="guidAddIconCmdSet" id="MyMenuGroup" />
        <Icon guid="testIcon" id="testIcon1" />
        <Strings>
            <ButtonText>My Command name</ButtonText>
        </Strings>
    </Button>
    ```

8. Pruebe su icono. Compile la solución y comience la depuración. En la instancia experimental, busque el comando. Debería mostrar el icono que agregó.

## <a name="see-also"></a>Vea también
- [Ampliación de menús y comandos](../extensibility/extending-menus-and-commands.md)
- [Referencia de esquema XML de VSCT](../extensibility/vsct-xml-schema-reference.md)
