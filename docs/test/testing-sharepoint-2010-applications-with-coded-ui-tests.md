---
title: Probar aplicaciones de SharePoint con pruebas automatizadas de IU
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 91d17857f1d20508041ad6c5daa90a962d6d30e6
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895449"
---
# <a name="test-sharepoint-applications-with-coded-ui-tests"></a>Probar aplicaciones de SharePoint con pruebas automatizadas de IU

Incluir pruebas de IU codificadas en una aplicación de SharePoint permite comprobar que toda la aplicación, incluidos sus controles de interfaz de usuario, funcionan correctamente. Las pruebas de IU codificadas también pueden validar valores y la lógica de la interfaz de usuario.

Para obtener más información sobre las ventajas de usar pruebas automatizadas de IU, consulte [Usar la automatización de IU para probar el código](../test/use-ui-automation-to-test-your-code.md).

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Requisitos**

- Visual Studio Enterprise

## <a name="create-a-coded-ui-test-for-a-sharepoint-app"></a>Crear una prueba automatizada de IU para una aplicación de SharePoint

[Crear pruebas automatizadas de IU](../test/use-ui-automation-to-test-your-code.md) para las aplicaciones de SharePoint es lo mismo que crear pruebas para otros tipos de aplicaciones. La grabación y la reproducción se admiten en todos los controles de la interfaz de **edición web**. La interfaz para seleccionar categorías y elementos web son todos los controles web estándar.

![Elementos web de SharePoint](../test/media/cuit_sharepoint.png)

> [!NOTE]
> Si graba una acción, valide las acciones antes de generar el código. Como hay varios comportamientos asociados con el desplazamiento del mouse, esta característica está activada de manera predeterminada. Tenga cuidado al quitar desplazamientos redundantes de las pruebas de IU codificadas. Puede hacerlo modificando el código de la prueba o usando el [editor de pruebas de IU codificadas](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

## <a name="test-office-controls-within-a-sharepoint-app"></a>Probar los controles de Office dentro de una aplicación de SharePoint

Para habilitar la automatización de algunos elementos web de Office en su aplicación de SharePoint, es necesario realizar algunas modificaciones mínimas en el código.

> [!NOTE]
> No es posible probar los controles de Visio y PowerPoint en una aplicación de SharePoint.

### <a name="excel-cell-controls"></a>Controles de celda de Excel

Para incluir controles de celda de Excel, hay que realizar algunos cambios en el código de la prueba de IU codificada.

> [!WARNING]
> Escribir texto en una celda de Excel, seguida de una acción de tecla de flecha, no se graba correctamente. Use el mouse para seleccionar celdas.

Si graba acciones en una celda vacía, tiene que modificar el código haciendo doble clic en la celda y, luego, realizando una operación de texto definida. Esto es necesario porque, al hacer clic en la celda, seguido de una acción de teclado, se activa `textarea` dentro de la celda. Grabar simplemente un `setvalue` en la celda vacía haría que se buscara el elemento `editbox` que no estará presente hasta que se haga clic en la celda. Por ejemplo:

```csharp
Mouse.DoubliClick(uiItemCell,new Point(31,14));
uiGridKeyboardInputEdit.Text=value;
```

Si graba acciones en una celda que no está vacía, la grabación será un poco más complicada, porque en cuanto agregue texto a una celda, se agregará un nuevo control \<div> como elemento secundario de la celda. El nuevo control \<div> contiene el texto que acaba de especificar. La grabadora necesita grabar acciones en el nuevo control \<div>, pero no puede porque el nuevo control \<div> no existirá hasta que se especifique la prueba. Tendrá que realizar los siguientes cambios en el código manualmente para acabar con este problema.

1. Vaya a la inicialización de la celda y establezca `RowIndex` y `ColumnIndex` como propiedades principales:

    ```csharp
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. RowIndex] = "3";
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. ColumnIndex] = "3";
    ```

2. Busque el elemento secundario `HtmlDiv` de la celda:

    ```csharp
    private UITestControl getControlToDoubleClick(HtmlCell cell)
    {
         if (String.IsNullOrEmpty(cell.InnerText)) return cell;
         HtmlDiv pane = new HtmlDiv(cell);
         pane.FilterProperties[HtmlDiv.PropertyNames.InnerText] = cell.InnerText;
         // Class is an important property in finding pane
         pane.FilterProperties[HtmlDiv.PropertyNames.Class] = "cv-nwr";
         UITestControlCollection panes = pane.FindMatchingControls();
         return panes[0];
    }
    ```

3. Agregue código para una acción de doble clic del mouse en `HtmlDiv`:

    ```csharp
    Mouse.DoubleClick(uIItemPane, new Point(31, 14)); )
    ```

4. Agregue código para texto establecido en `TextArea`:

    ```csharp
    uIGridKeyboardInputEdit.Text = value; }
    ``

## See also

- [Use UI automation to test your code](../test/use-ui-automation-to-test-your-code.md)
- [Create SharePoint solutions](../sharepoint/create-sharepoint-solutions.md)
- [Verify and debug SharePoint code](../sharepoint/verifying-and-debugging-sharepoint-code.md)
- [Build and debug SharePoint solutions](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Profile the performance of SharePoint applications](../sharepoint/profiling-the-performance-of-sharepoint-applications.md)
