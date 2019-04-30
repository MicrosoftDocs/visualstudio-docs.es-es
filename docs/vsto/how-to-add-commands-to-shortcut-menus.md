---
title: Procedimiento Agregar comandos a menús contextuales
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office menus, creating
- Office development in Visual Studio, context menus
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3b20b10a37908e2c9744aeac63bb3eda091da478
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62826410"
---
# <a name="how-to-add-commands-to-shortcut-menus"></a>Procedimiento Agregar comandos a menús contextuales
  En este tema se muestra cómo agregar comandos a un menú contextual en una aplicación de Office mediante el uso de un complemento de VSTO.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

### <a name="to-add-commands-to-shortcut-menus-in-office"></a>Para agregar comandos a los menús contextuales de Office

1. Agregue un elemento **XML de cinta** a un proyecto de nivel de documento o de complemento de VSTO. Para obtener más información, vea [Cómo: Introducción a la personalización de la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md). En

2. el**Exploado de soluciones**, seleccione **ThisAddIn.cs** o **ThisAddIn.vb**.

3. En la barra de menús, elija **Ver** > **Código**.

     El archivo de clase **ThisAddin** se abrirá en el Editor de código.

4. Agregue el siguiente código a la clase **ThisAddin** . Este código invalida el método `CreateRibbonExtensibilityObject` y devuelve la clase XML Ribbon a la aplicación de Office.

     [!code-csharp[Trin_WordAddIn_Menus#1](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#1)]
     [!code-vb[Trin_WordAddIn_Menus#1](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#1)]

5. En el **Explorador de soluciones**, seleccione el archivo XML de cinta. De forma predeterminada, el archivo XML de cinta se denomina *Ribbon1.xml*.

6. En la barra de menús, elija **Ver** > **Código**.

     Se abrirá el archivo de código XML de cinta de opciones en el Editor de código.

7. En el Editor de código, agregue el código XML que describe el menú contextual y el control que quiere agregar al menú contextual.

     En el ejemplo siguiente se agrega un botón, un menú y un control de galería al menú contextual de un documento de Word. El id. del control de este menú contextual es ContextMenuText. Para obtener una lista completa de control de acceso directo de Office 2010 identificadores, vea [los archivos de Ayuda de Office 2010: Identificadores de control de interfaz de usuario fluent Office](http://go.microsoft.com/fwlink/?LinkID=181052).

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <customUI xmlns="http://schemas.microsoft.com/office/2009/07/customui">
      <contextMenus>
        <contextMenu idMso="ContextMenuText">
          <button id="MyButton" label="My Button" insertBeforeMso="HyperlinkInsert" onAction="GetButtonID" />
          <menu id="MySubMenu" label="My Submenu" >
            <button id="MyButton2" label="Button on submenu" />
          </menu>
          <gallery id="galleryOne" label="My Gallery">
            <item id="item1" imageMso="HappyFace" />
            <item id="item2" imageMso="HappyFace" />
            <item id="item3" imageMso="HappyFace" />
            <item id="item4" imageMso="HappyFace" />
          </gallery>
        </contextMenu>
      </contextMenus>
    </customUI>
    ```

8. En el **Explorador de soluciones**, elija **MyRibbon.cs** o **MyRibbon.vb**.

9. Agregue un método de devolución de llamada a la `Ribbon1` clase para cada control que desea administrar.

     El siguiente método de devolución de llamada controla el botón **Mi botón** . Este código agrega una cadena al documento activo en la posición actual del cursor.

     [!code-vb[Trin_WordAddIn_Menus#2](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/ribbon1.vb#2)]
     [!code-csharp[Trin_WordAddIn_Menus#2](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/ribbon1.cs#2)]

## <a name="see-also"></a>Vea también
- [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)
- [Tutorial: Crear menús contextuales para marcadores](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)
- [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
- [Personalizar los menús contextuales de Office 2010](http://go.microsoft.com/fwlink/?LinkId=182186)
