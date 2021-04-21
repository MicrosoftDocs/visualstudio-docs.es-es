---
title: 'Cómo: Agregar comandos a menús contextuales'
description: Obtenga información sobre cómo agregar comandos a un menú contextual de una aplicación de Office mediante un complemento de VSTO.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office menus, creating
- Office development in Visual Studio, context menus
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 276dc7b8094c495a1b3896a4a93a068b1005c8d5
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828454"
---
# <a name="how-to-add-commands-to-shortcut-menus"></a>Cómo: Agregar comandos a menús contextuales
  En este tema se muestra cómo agregar comandos a un menú contextual de una aplicación de Office mediante un complemento de VSTO.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

### <a name="to-add-commands-to-shortcut-menus-in-office"></a>Para agregar comandos a los menús contextuales de Office

1. Agregue un elemento **XML de cinta** a un proyecto de nivel de documento o de complemento de VSTO. Para obtener más información, [vea Cómo: Introducción a la personalización de la cinta de opciones.](../vsto/how-to-get-started-customizing-the-ribbon.md) En

2. el **Exploado de soluciones**, seleccione **ThisAddIn.cs** o **ThisAddIn.vb**.

3. En la barra de menús, elija **Ver** > **Código**.

     El archivo de clase **ThisAddin** se abrirá en el Editor de código.

4. Agregue el siguiente código a la clase **ThisAddin** . Este código invalida el método `CreateRibbonExtensibilityObject` y devuelve la clase XML Ribbon a la aplicación de Office.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb" id="Snippet1":::

5. En el **Explorador de soluciones**, seleccione el archivo XML de cinta. De forma predeterminada, el archivo XML de la cinta de opciones se *denominaRibbon1.xml*.

6. En la barra de menús, elija **Ver** > **Código**.

     Se abrirá el archivo de código XML de cinta de opciones en el Editor de código.

7. En el Editor de código, agregue el código XML que describe el menú contextual y el control que quiere agregar al menú contextual.

     En el ejemplo siguiente se agrega un botón, un menú y un control de galería al menú contextual de un documento de Word. El id. del control de este menú contextual es ContextMenuText. Para obtener una lista completa de los identificadores de control de acceso directo de Office 2010, vea Archivos de ayuda de [Office 2010:](https://www.microsoft.com/download/details.aspx?id=6627)Identificadores de control de interfaz de usuario fluida de Office .

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

9. Agregue un método de devolución de llamada `Ribbon1` a la clase para cada control que desee controlar.

     El siguiente método de devolución de llamada controla el botón **Mi botón** . Este código agrega una cadena al documento activo en la posición actual del cursor.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/ribbon1.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/ribbon1.cs" id="Snippet2":::

## <a name="see-also"></a>Consulte también
- [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)
- [Tutorial: Crear menús contextuales para marcadores](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)
- [Parámetros opcionales en soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
- [Personalización de menús contextuales en Office 2010](/previous-versions/office/developer/office-2010/ee691832(v=office.14))
