---
title: Anatomía de una prueba automatizada de IU | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests
ms.assetid: 9c5d82fc-3fb7-4bb1-a9ac-ac1fa3a4b500
caps.latest.revision: 25
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 305c0b33b52c54e7d241b4e86e974d25e58d1e51
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660693"
---
# <a name="anatomy-of-a-coded-ui-test"></a>Anatomía de una prueba de IU codificada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cuando se crea una prueba de IU codificada en un proyecto de prueba de IU codificada, se agregan varios archivos a la solución. En este tema, se explorarán estos archivos con una prueba de IU codificada de ejemplo.

 **Requisitos**

- Visual Studio Enterprise

## <a name="contents-of-a-coded-ui-test"></a>Contenido de una prueba de IU codificada
 Cuando se crea una prueba automatizada de IU, el **generador de pruebas automatizadas de IU** crea un mapa de la interfaz de usuario que se va a someter a prueba, e incluye también los métodos de prueba, los parámetros y las aserciones de todas las pruebas. También crea un archivo de clase para cada prueba.

|Archivo|Contenido|¿Se puede editar?|
|----------|--------------|---------------|
|[UIMap.Designer.cs](#UIMapDesignerFile)|[Sección Declaraciones](#UIMapDesignerFile)<br /><br /> [Clase UIMap](#UIMapClass) (parcial, generada automáticamente)<br /><br /> [Métodos](#UIMapMethods)<br /><br /> [Propiedades](#UIMapProperties)|No|
|[UIMap.cs](#UIMapCS)|[Clase UIMap](#UIMapCS) (parcial)|Sí|
|[CodedUITest1.cs](#CodedUITestCS)|[Clase CodedUITest1](#CodedUITestCS)<br /><br /> [Métodos](#CodedUITestMethods)<br /><br /> [Propiedades](#CodedUITestProperties)|Sí|
|[UIMap.uitest](#UIMapuitest)|La asignación XML de la interfaz de usuario para la prueba.|No|

### <a name="UIMapDesignerFile"></a> UIMap.Designer.cs
 Este archivo contiene código que se crea automáticamente desde el **generador de pruebas automatizadas de IU** cuando se crea una prueba. Este archivo se crea de nuevo cada vez que cambia una prueba, por lo tanto, no se puede agregar código o modificar el código que contiene.

#### <a name="declarations-section"></a>Sección Declaraciones
 Esta sección incluye las declaraciones siguientes para una interfaz de usuario de Windows.

```csharp
using System;
using System.CodeDom.Compiler;
using System.Collections.Generic;
using System.Drawing;
using System.Text.RegularExpressions;
using System.Windows.Input;
using Microsoft.VisualStudio.TestTools.UITest.Extension;
using Microsoft.VisualStudio.TestTools.UITesting;
using Microsoft.VisualStudio.TestTools.UITesting.WinControls;
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Keyboard = Microsoft.VisualStudio.TestTools.UITesting.Keyboard;
using Mouse = Microsoft.VisualStudio.TestTools.UITesting.Mouse;
using MouseButtons = System.Windows.Forms.MouseButtons;
```

 Para una interfaz de usuario (UI) de Windows, se incluye el espacio de nombres <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls>. Para la interfaz de usuario de una página web, el espacio de nombres sería <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls>. Para una interfaz de usuario de Windows Presentation Foundation, el espacio de nombres sería <xref:Microsoft.VisualStudio.TestTools.UITesting.WpfControls>.

#### <a name="UIMapClass"></a> Clase UIMap
 La sección siguiente del archivo es la clase [UIMap](/previous-versions/dd580454(v=vs.140)).

```
[GeneratedCode("Coded UITest Builder", "10.0.21221.0")]
public partial class UIMap
```

 El código de clase comienza con un elemento <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> que se aplica a la clase (declarada como clase parcial). Observará que el atributo también se aplica a todas las clases restantes de este archivo. El otro archivo que puede contener más código para esta clase es `UIMap.cs` (se describe más adelante).

 La clase `UIMap` generada incluye código para cada uno de los métodos que se ha especificado al registrar la prueba.

```
public void LaunchCalculator()
public void AddItems()
public void VerifyTotal()
public void CleanUp()
```

 Esta parte de la clase [UIMap](/previous-versions/dd580454(v=vs.140)) también incluye el código generado para las distintas propiedades que requieren los métodos.

```
public virtual LaunchCalculatorParams LaunchCalculatorParams
public virtual AddItemsParams AddItemsParams
public virtual VerifyTotalExpectedValues VerifyTotalExpectedValues
public virtual CalculateItemsParams CalculateItemsParams
public virtual VerifyMathAppTotalExpectedValues
    VerifyMathAppTotalExpectedValues
public UIStartMenuWindow UIStartMenuWindow
public UIRunWindow UIRunWindow
public UICalculatorWindow UICalculatorWindow
public UIStartWindow UIStartWindow
public UIMathApplicationWindow UIMathApplicationWindow
```

##### <a name="UIMapMethods"></a> Métodos de UIMap
 Cada método tiene una estructura similar a la del método `AddItems()`. Esto se explica con mayor detalle debajo del código, que se muestra con saltos de línea para aportar claridad.

```
/// <summary>
/// AddItems - Use 'AddItemsParams' to pass parameters into this method.
/// </summary>
public void AddItems()
{
    #region Variable Declarations
    WinControl uICalculatorDialog =
        this.UICalculatorWindow.UICalculatorDialog;
    WinEdit uIItemEdit =
        this.UICalculatorWindow.UIItemWindow.UIItemEdit;
    #endregion

    // Type '{NumPad7}' in 'Calculator' Dialog
    Keyboard.SendKeys(uICalculatorDialog,
        this.AddItemsParams.UICalculatorDialogSendKeys,
        ModifierKeys.None);

    // Type '{Add}{NumPad2}{Enter}' in 'Unknown Name' text box
    Keyboard.SendKeys(uIItemEdit,
        this.AddItemsParams.UIItemEditSendKeys,
        ModifierKeys.None);
}
```

 El comentario de resumen de cada definición de método indica la clase se debe usar para los valores de parámetro de dicho método. En este caso se trata de la clase `AddItemsParams`, que se define más adelante en el archivo `UIMap.cs` y también constituye el tipo de valor que devuelve la propiedad `AddItemsParams`.

 En la parte superior del código de método existe una región `Variable Declarations`, que define las variables locales para los objetos de interfaz de usuario que usará el método.

 En este método, `UIItemWindow` y `UIItemEdit` son propiedades a las que se accede con la clase `UICalculatorWindow`, tal y como se define más adelante en el archivo `UIMap.cs`.

 A continuación se encuentran las líneas que envían texto desde el teclado hasta la aplicación Calculadora mediante las propiedades del objeto `AddItemsParams`.

 El método `VerifyTotal()` tiene una estructura muy similar e incluye el código de aserción siguiente.

```
// Verify that 'Unknown Name' text box's property 'Text' equals '9. '
Assert.AreEqual(
    this.VerifyTotalExpectedValues.UIItemEditText,
    uIItemEdit.Text);
```

 El nombre del cuadro de texto se define como desconocido porque el desarrollador de la aplicación Calculadora de Windows no ha proporcionado un nombre disponible públicamente para el control. El método <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=fullName> genera un error cuando el valor real no es igual al valor esperado. En este caso, la prueba podría generar errores. Observe también que el valor esperado incluye un separador decimal seguido de un espacio. Si alguna vez tiene que modificar la funcionalidad de esta prueba concreta, deberá permitir este separador decimal y el espacio.

##### <a name="UIMapProperties"></a> Propiedades de UIMap
 También se usa un código muy estandarizado para cada propiedad a través de la clase. El código siguiente para la propiedad `AddItemsParams` se usa en el método `AddItems()`.

```
public virtual AddItemsParams AddItemsParams
{
    get
    {
        if ((this.mAddItemsParams == null))
        {
            this.mAddItemsParams = new AddItemsParams();
        }
        return this.mAddItemsParams;
    }
}
```

 Observe que la propiedad usa una variable local privada denominada `mAddItemsParams`, que contiene el valor antes de devolverlo. Los nombres de propiedad y clase que se devuelven del objeto son los mismos. La clase se define más adelante en el archivo `UIMap.cs`.

 Las clases que se devuelven desde las propiedades tienen una estructura similar. La siguiente es la clase `AddItemsParams`.

```
/// <summary>
/// Parameters to be passed into 'AddItems'
/// </summary>
[GeneratedCode("Coded UITest Builder", "10.0.21221.0")]
public class AddItemsParams
{
    #region Fields
    /// <summary>
    /// Type '{NumPad7}' in 'Calculator' Dialog
    /// </summary>
    public string UICalculatorDialogSendKeys = "{NumPad7}";

    /// <summary>
    /// Type '{Add}{NumPad2}{Enter}' in 'Unknown Name' text box
    /// </summary>
    public string UIItemEditSendKeys = "{Add}{NumPad2}{Enter}";
    #endregion
}
```

 Al igual que ocurre con todas las clases del archivo `UIMap.cs`, esta clase comienza con <xref:System.CodeDom.Compiler.GeneratedCodeAttribute>. En esta pequeña clase existe un área `Fields` que define las cadenas que se deben usar como parámetros para el método <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A?displayProperty=fullName> que, a su vez, se usa en el método `UIMap.AddItems()` (analizado anteriormente). Puede escribir código para reemplazar los valores de estos campos de cadena, antes de llamar al método donde se usan estos parámetros.

### <a name="UIMapCS"></a> UIMap.cs
 De forma predeterminada, este archivo contiene una clase `UIMap` parcial, que no tiene métodos ni propiedades.

#### <a name="uimap-class"></a>Clase UIMap
 Aquí puede crear código personalizado para extender la funcionalidad de la clase [UIMap](/previous-versions/dd580454(v=vs.140)). El **generador de pruebas automatizadas de IU** no regenerará el código que cree en este archivo cada vez que se modifique una prueba.

 Todos los componentes de [UIMap](/previous-versions/dd580454(v=vs.140)) pueden usar los métodos y las propiedades de cualquier otro componente de la clase [UIMap](/previous-versions/dd580454(v=vs.140)).

### <a name="CodedUITestCS"></a> CodedUITest1.cs
 El **generador de pruebas automatizadas de IU** genera este archivo pero no lo recrea cada vez que se modifica la prueba, por lo que puede modificar el código que contiene. El nombre del archivo se genera a partir del nombre que se especifica para la prueba cuando se crea.

#### <a name="codeduitest1-class"></a>Clase CodedUITest1
 De forma predeterminada, este archivo contiene la definición de una sola clase.

```
[CodedUITest]
public class CodedUITest1
```

 El [CodedUITestAttribute](/previous-versions/visualstudio/visual-studio-2013/ff430233(v=vs.120)) se aplica a la clase de forma automática, lo que permite al marco de pruebas reconocerlo como una extensión de pruebas. Asimismo, tenga en cuenta que no es una clase parcial. Este archivo contiene todo el código de clase.

##### <a name="CodedUITestProperties"></a> Propiedades CodedUITest1
 La clase contiene dos propiedades predeterminadas que se encuentran en la parte inferior del archivo. No se deben modificar.

```
/// <summary>
/// Gets or sets the test context which provides
/// information about and functionality for the current test run.
///</summary>
public TestContext TestContext
public UIMap UIMap
```

##### <a name="CodedUITestMethods"></a> Métodos CodedUITest1
 De forma predeterminada, la clase solo contiene un método.

```
public void CodedUITestMethod1()
```

 Este método llama a los distintos métodos `UIMap` que se especificaron al registrar la prueba, tal y como se describe en la sección sobre la [clase UIMap](#UIMapClass).

 Si la región `Additional test attributes` no incluye comentarios, significa que contiene dos métodos opcionales.

```
// Use TestInitialize to run code before running each test
[TestInitialize()]
public void MyTestInitialize()
{
    // To generate code for this test, select "Generate Code for Coded
    // UI Test" from the shortcut menu and select one of the menu items.
    // For more information on generated code, see
    // http://go.microsoft.com/fwlink/?LinkId=179463

    // You could move this line from the CodedUITestMethod1() method
    this.UIMap.LaunchCalculator();
}

// Use TestCleanup to run code after each test has run
[TestCleanup()]
public void MyTestCleanup()
{
    // To generate code for this test, select "Generate Code for Coded
    // UI Test" from the shortcut menu and select one of the menu items.
    // For more information on generated code, see
    // http://go.microsoft.com/fwlink/?LinkId=179463

    // You could move this line from the CodedUITestMethod1() method
    this.UIMap.CloseCalculator();
}
```

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute> se ha aplicado al método `MyTestInitialize()`, lo que indica al marco de pruebas que debe llamar a este método antes que a ningún otro método de prueba. Del mismo modo, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute> se ha aplicado al método `MyTestCleanup()`, lo que indica al marco de pruebas que debe llamar a este método después de que se haya llamado a todos los métodos de prueba restantes. El uso de estos métodos es opcional. Para esta prueba, puede llamarse al método `UIMap.LaunchCalculator()` desde `MyTestInitialize()`, y al método `UIMap.CloseCalculator()` desde `MyTestCleanup()` (en lugar de desde `CodedUITest1Method1()`).

 Si agrega más métodos a esta clase con [CodedUITestAttribute](/previous-versions/visualstudio/visual-studio-2013/ff430233(v=vs.120)), el marco de pruebas llamará a cada método como parte de la prueba.

### <a name="UIMapuitest"></a> UIMap.uitest
 Se trata de un archivo XML que representa la estructura de la grabación de la prueba de IU codificada y de todos sus componentes. Entre ellos se incluyen las acciones y las clases, además de los métodos y las propiedades de estas últimas. El archivo [UIMap.Designer.cs](#UIMapDesignerFile) contiene el código que el generador de pruebas automatizadas de IU crea para reproducir la estructura de la prueba y proporciona la conexión con el marco de pruebas.

 El archivo `UIMap.uitest` no se puede editar directamente. Pero puede modificar la prueba con el generador de pruebas automatizadas de IU, lo que modifica automáticamente los archivos `UIMap.uitest` y [UIMap.Designer.cs](#UIMapDesignerFile).

## <a name="see-also"></a>Vea también

- [UIMap](/previous-versions/dd580454(v=vs.140))
- <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls>
- <xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls>
- <xref:Microsoft.VisualStudio.TestTools.UITesting.WpfControls>
- <xref:System.CodeDom.Compiler.GeneratedCodeAttribute>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A?displayProperty=fullName>
- [CodedUITestAttribute](/previous-versions/visualstudio/visual-studio-2013/ff430233(v=vs.120))
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestInitializeAttribute>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCleanupAttribute>
- [Usar Automatización de la interfaz de usuario para probar el código](../test/use-ui-automation-to-test-your-code.md)
- [Crear pruebas de IU codificadas](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)
- [Procedimientos recomendados para las pruebas de IU codificadas](../test/best-practices-for-coded-ui-tests.md)
- [Probar una aplicación grande con varios mapas de IU](../test/testing-a-large-application-with-multiple-ui-maps.md)
- [Configuraciones y plataformas compatibles con las pruebas de IU codificadas y las grabaciones de acciones](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
