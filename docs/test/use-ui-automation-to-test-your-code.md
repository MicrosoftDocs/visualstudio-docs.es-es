---
title: Pruebas automatizadas de IU
ms.date: 12/04/2018
ms.topic: conceptual
f1_keywords:
- vs.codedUITest
- vs.codedUITest.recorder
- vs.codedUITest.testbuilder
- vs.codedUITest.addAssertions
- vs.codedUITest.createdialog
helpviewer_keywords:
- automated tests, testing UI interface
- coded UI test
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b6798af3630f81aa50eaae05b23b6844dcba1f38
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62973558"
---
# <a name="use-ui-automation-to-test-your-code"></a>Usar la automatización de la interfaz de usuario para probar el código

Las pruebas automatizadas que controlan la aplicación a través de la interfaz de usuario se conocen como *pruebas automatizadas de IU* (CUIT) en Visual Studio. Estas pruebas incluyen unas pruebas funcionales de los controles de la interfaz de usuario. Permiten comprobar si toda la aplicación, incluida la interfaz de usuario, funciona correctamente. Las pruebas de IU codificadas son especialmente útiles donde haya una validación o cualquier otra lógica en la interfaz de usuario, por ejemplo, en una página web. También se suelen usar para automatizar una prueba manual existente.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

Como se muestra en la ilustración siguiente, una experiencia típica de desarrollo podría ser aquella donde, inicialmente, el usuario se limite a compilar la aplicación y a hacer clic en los controles de la interfaz de usuario a fin de comprobar que todo funciona correctamente. Después, es posible que decida crear una prueba automatizada de manera que no sea necesario seguir probando la aplicación manualmente. Según la funcionalidad concreta que se prueba en la aplicación, puede escribir código para una prueba funcional o bien una prueba de integración que es posible que incluya o no la realización de pruebas en el nivel de interfaz de usuario. Si quiere tener acceso directamente a alguna lógica de negocios, puede codificar una prueba unitaria. Sin embargo, en algunas circunstancias, puede ser beneficioso incluir pruebas de los diversos controles de IU en la aplicación. Una prueba automatizada de IU puede comprobar que la renovación de código no afecte a la funcionalidad de la aplicación.

![Pruebas durante el desarrollo de la aplicación](../test/media/cuit_overview.png)

Crear una prueba de IU codificada es fácil. Basta con efectuar la prueba manualmente mientras el **generador de pruebas automatizadas de IU** se ejecuta en segundo plano. También puede especificar qué valores deben aparecer en campos concretos. El **generador de pruebas automatizadas de IU** registra las acciones y genera código a partir de estas. Después de crear la prueba, puede editarla en un editor especializado que permita modificar la secuencia de acciones.

Como alternativa, si tiene un caso de prueba que se haya registrado en Microsoft Test Manager, puede generar código a partir de este. Para obtener más información, consulte [Grabar y reproducir pruebas manuales](/azure/devops/test/mtm/record-play-back-manual-tests?view=vsts).

El editor y el **generador especializados de pruebas automatizadas de IU** facilitan la creación y la edición de pruebas automatizadas de IU, aunque sus conocimientos principales se concentren en las pruebas en lugar de en la codificación. Pero si es un desarrollador y desea extender la prueba de forma más avanzada, el código se estructura para que sea fácil de copiar y adaptar. Por ejemplo, puede registrar una prueba para comprar algo en un sitio web y, a continuación, editar el código generado para agregar un bucle que compre muchos elementos.

**Requisitos**

- Visual Studio Enterprise
- Componente Prueba automatizada de IU

Para obtener más información sobre las configuraciones y plataformas compatibles con las pruebas automatizadas de IU, vea [Plataformas compatibles](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md).

## <a name="install-the-coded-ui-test-component"></a>Instalar el componente Prueba automatizada de IU

Para acceder a las plantillas y herramientas de pruebas automatizadas de IU, instale el componente **Prueba automatizada de IU** de Visual Studio.

1. Inicie el **Instalador de Visual Studio** eligiendo **Herramientas** > **Obtener herramientas y características**.

1. En el **Instalador de Visual Studio**, elija la pestaña **Componentes individuales** y desplácese hacia abajo hasta la sección **Depuración y pruebas**. Seleccione el componente **Prueba automatizada de IU**.

   ![Componente Prueba automatizada de IU](media/coded-ui-test-component.png)

1. Seleccione **Modificar**.

## <a name="create-a-coded-ui-test"></a>Crear una prueba de IU codificada

1. Cree un proyecto de prueba de IU codificada.

   Las pruebas de IU codificadas deben incluirse en un proyecto de prueba de IU codificada. Si aún no tiene un proyecto de este tipo, cree uno. Elija **Archivo** > **Nuevo** > **Proyecto**. Busque la plantilla de proyecto **Proyecto de prueba automatizada de IU** y selecciónela.

   ::: moniker range="vs-2017"

   ![Plantilla Proyecto de prueba de IU codificada en el cuadro de diálogo Nuevo proyecto](media/coded-ui-test-project-template.png)

   ::: moniker-end

   > [!NOTE]
   > Si no ve la plantilla **Proyecto de prueba automatizada de IU**, necesitará [instalar el componente de prueba automatizada de IU](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component).

2. Agregue un archivo de prueba de IU codificada.

     Si acaba de crear un proyecto de IU codificada, el primer archivo de CUIT se agrega automáticamente. Para agregar otro archivo de prueba, abra el menú contextual del proyecto de prueba de IU codificada, en el **Explorador de soluciones** y luego elija **Agregar** > **Prueba de IU codificada**.

     En el cuadro de diálogo **Generar código para prueba automatizada de IU**, elija **Grabar acciones** > **Editar asignación de IU o agregar aserciones**.

     ![Cuadro de diálogo Generar código para prueba de IU codificada](media/generate-code-for-coded-ui-test.png)

     Aparece el cuadro de diálogo **Generador de pruebas automatizadas de IU**.

     ![Generador de pruebas de IU codificadas](../test/media/codedui_testbuilder.png)

3. Grabe una secuencia de acciones.

     **Para iniciar la grabación**, elija el icono **Grabar**. Realice las acciones que desea probar en la aplicación, incluido el inicio de la aplicación si es necesario. Por ejemplo, si va a probar una aplicación web, puede iniciar un explorador, navegar al sitio web e iniciar sesión en la aplicación.

     **Para pausar la grabación**, por ejemplo, si tiene que encargarse del correo entrante, elija **Pausar**.

    > [!WARNING]
    > Todas las acciones realizadas en el escritorio se grabarán. Pause la grabación si está realizando acciones que puedan hacer que los datos confidenciales se incluyan en la grabación.

     **Para eliminar acciones** grabadas por error, elija **Editar pasos**.

     **Para generar código** que replique las acciones, elija el icono **Generar código** y escriba un nombre y una descripción para el método de prueba de IU codificada.

4. Compruebe los valores de los campos de la interfaz de usuario, como por ejemplo cuadros de texto.

     Elija **Agregar aserciones** en el **Generador de pruebas automatizadas de IU** y después seleccione un control de IU en la aplicación en ejecución. En la lista de propiedades que aparece, seleccione una propiedad como **Text** en un cuadro de texto. En el menú contextual, elija **Agregar aserción**. En el cuadro de diálogo, seleccione el operador de comparación, el valor de comparación y el mensaje de error.

     Cierre la ventana de aserción y elija **Generar código**.

     ![Pruebas de IU codificadas dirigidas a un elemento](../test/media/codedui_1.png)

    > [!TIP]
    > Alterne entre el registro de acciones y la comprobación de valores. Genere código al final de cada secuencia de acciones o comprobaciones. Si lo desea, podrá insertar nuevas acciones y comprobaciones más adelante.

     Para obtener más detalles, vea [Validar las propiedades de los controles](#validate-the-properties-of-ui-controls).

5. Vea el código de prueba generado.

     Para ver el código generado, cierre la ventana del generador de pruebas de IU. En el código, puede ver los nombres que ha asignado a cada paso. El código está en el archivo de CUIT que creó:

    ```csharp
    [CodedUITest]
    public class CodedUITest1
    { ...
      [TestMethod]
      public void CodedUITestMethod1()
      {
          this.UIMap.AddTwoNumbers();
          this.UIMap.VerifyResultValue();
          // To generate more code for this test, select
          // "Generate Code" from the shortcut menu.
      }
    }
    ```

6. Agregue más acciones y aserciones.

   Coloque el cursor en el punto adecuado del método de prueba y después, en el menú contextual, elija **Generar código para prueba de IU codificada**. El nuevo código se insertará en ese punto.

7. Edite los detalles de las acciones de prueba y las aserciones.

     Abra *UIMap.uitest*. Este archivo se abre en el **Editor de pruebas automatizadas de IU**, donde puede editar cualquier secuencia de acciones que haya grabado, así como las aserciones.

     ![Editor de pruebas de IU codificadas](../test/media/cuit_editor_edit.png)

     Para obtener más información, vea [Editar pruebas automatizadas de IU con el Editor de pruebas automatizadas de IU](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

8. Ejecute la prueba.

   Use el Explorador de pruebas o abra el menú contextual del método de prueba y después elija **Ejecutar pruebas**. Para obtener más información sobre cómo ejecutar pruebas, vea [Ejecutar pruebas unitarias con el Explorador de pruebas](../test/run-unit-tests-with-test-explorer.md) y *Opciones adicionales para ejecutar pruebas de IU codificadas* en la sección [Pasos adicionales](#whats-next) al final de este tema.

Las secciones restantes de este tema proporcionan más detalles sobre los pasos de este procedimiento.

Para obtener un ejemplo más detallado, vea [Tutorial: Crear, editar y mantener una prueba automatizada de IU](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md). En el tutorial, se creará una aplicación Windows Presentation Foundation (WPF) simple para mostrar cómo crear, modificar y mantener una prueba de IU codificada. El tutorial proporciona soluciones para la corrección de pruebas que han sido interrumpidas por diversos problemas de sincronización y de control de refactorización.

## <a name="start-and-stop-the-application-under-test"></a>Iniciar y detener la aplicación sometida a pruebas

Si no quiere iniciar y detener la aplicación, el explorador o la base de datos por separado para cada prueba, tiene varias opciones:

- Si no desea grabar las acciones de inicio de la aplicación en pruebas, debe iniciar su aplicación antes de elegir el icono **Grabar**.

- Al final de una prueba, finaliza el proceso en el que se ejecuta la prueba. Si la aplicación se inició en la prueba, esta suele cerrarse.  Si no desea que la prueba cierre la aplicación al finalizar, agregue un archivo *.runsettings* a la solución y use la opción `KeepExecutorAliveAfterLegacyRun`. Para obtener más información, consulte [Configurar pruebas unitarias usando un archivo .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

- Agregue un método que inicialice la prueba, identificado mediante un atributo `[TestInitialize]`, que ejecute código al comienzo de cada método de prueba. Por ejemplo, puede iniciar la aplicación desde el método TestInitialize.

- Agregue un método que de limpieza de pruebas, identificado mediante un atributo `[TestCleanup]`, que ejecute código al final de cada método de prueba. Por ejemplo, el método para cerrar la aplicación podría invocarse desde el método TestCleanup.

## <a name="validate-the-properties-of-ui-controls"></a>Validar las propiedades de los controles de IU

Puede usar el **Generador de pruebas de IU codificadas** para agregar un control de interfaz de usuario a <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> para la prueba o generar código para un método de validación que usa una aserción para un control de IU.

Para generar aserciones para los controles de IU, elija la herramienta **Agregar aserciones** del **Generador de pruebas automatizadas de IU** y arrástrela al control de la aplicación en pruebas que quiere comprobar si es correcto. Cuando el cuadro rodee el control, suelte el mouse. El código de clase de control se crea inmediatamente en el archivo *UIMap.Designer.cs*.

![Pruebas de IU codificadas dirigidas a un elemento](../test/media/codedui_1.png)

Las propiedades de este control se muestran ahora en el cuadro de diálogo **Agregar aserciones**.

Otra forma de navegar a un control determinado es elegir la flecha **(<<)** para expandir la vista de la **Asignación de controles de IU**. Para buscar un control primario, relacionado o secundario, haga clic en cualquier parte del mapa y use las teclas de dirección para moverse por el árbol.

![Propiedades de pruebas de IU codificadas](../test/media/codedui_2.png)

> [!TIP]
> Si no ve las propiedades cuando se selecciona un control en la aplicación o no ve el control en la asignación de controles de interfaz de usuario, compruebe que el control tiene un identificador único en el código de aplicación. El identificador único puede ser un atributo ID HTML o un UId de WPF.

A continuación, abra el menú contextual del control de IU que desea comprobar y elija **Agregar aserción**. En el cuadro de diálogo **Agregar aserción**, seleccione **Comparador** para la aserción, por ejemplo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A> y escriba el valor para esta en **Valor de comparación**.

![Aserciones de pruebas de IU codificadas](../test/media/codedui_3.png)

Cuando haya agregado todas las aserciones para la prueba, elija **Aceptar**.

Para generar el código de las aserciones y agregar el control a la asignación de la interfaz de usuario, elija el icono **Generar código**. Escriba un nombre para el método de prueba de IU codificada y una descripción para el método, que se agregará como comentarios sobre el método. Elija **Agregar y generar**. A continuación, elija el icono **Cerrar** para cerrar el **Generador de pruebas de IU codificadas**. Esto genera código similar al siguiente. Por ejemplo, si el nombre que escribió es `AssertForAddTwoNumbers`, el código tendrá el aspecto mostrado en este ejemplo:

- Agrega una llamada al método de aserción AssertForAddTwoNumbers en el método de prueba del archivo de prueba de IU codificada:

    ```csharp
    [TestMethod]
    public void CodedUITestMethod1()
    {
        this.UIMap.AddTwoNumbers();
        this.UIMap.AssertForAddTwoNumbers();
    }
    ```

     Puede editar este archivo para cambiar el orden de los pasos y aserciones o crear nuevos métodos de prueba. Para agregar más código, coloque el cursor en el método de prueba y, en el menú contextual, elija **Generar código para prueba de IU codificada**.

- Agrega un método denominado `AssertForAddTwoNumbers` a la asignación de interfaz de usuario (*UIMap.uitest*). Este archivo se abre en el **Editor de pruebas automatizadas de IU**, donde puede editar las aserciones.

     ![Editar aserción con el Editor de pruebas de IU codificadas](../test/media/cuit_editor_assert.png)

     Para obtener más información, vea [Editar pruebas automatizadas de IU con el Editor de pruebas automatizadas de IU](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

     También puede ver el código generado del método de aserción en *UIMap.Designer.cs*. Sin embargo, no debe editar este archivo. Si quiere crear una versión adaptada del código, copie los métodos en otro archivo, como *UIMap.cs*, cambie el nombre de los métodos y edítelos en directamente en este.

    ```csharp
    public void AssertForAddTwoNumbers()
    {
        ...
    }
    ```

### <a name="select-a-hidden-control-using-the-keyboard"></a>Seleccionar un control oculto mediante el teclado

Si el control que quiere seleccionar pierde el foco y desaparece cuando intenta seleccionar la herramienta **Agregar aserciones** en el **Generador de pruebas automatizadas de IU**:

A veces, al agregar controles y validar sus propiedades, es posible que tenga que usar el teclado. Por ejemplo, al intentar grabar una prueba automatizada de IU que usa un control de menú de botón derecho, la lista de elementos del menú del control perderá el foco y desaparecerá cuando se intente seleccionar la herramienta **Agregar aserciones** desde el **Generador de pruebas automatizadas de IU**. Esto se muestra en la ilustración siguiente, donde el menú de botón derecho de Internet Explorer pierde el foco y desaparece si intenta seleccionarlo con la herramienta **Agregar aserciones**.

![PruebaAutomatizadaIU&#95;TecladoSelecciónControl](../test/media/codeduitest_selectcontrolkeyboard.png)

Para usar el teclado para seleccionar un control de IU, mantenga el mouse sobre el control. A continuación, mantenga presionadas las teclas **Ctrl** e **I** al mismo tiempo. Suelte las teclas. El **Generador de pruebas automatizadas de IU** registra el control.

#### <a name="manually-record-mouse-hovers"></a>Grabar manualmente eventos de mantenimiento del mouse

Si no puede grabar un movimiento del mouse sobre un control:

En algunas circunstancias, un control determinado que se usa en una prueba de IU programada podría requerir que se use el teclado para grabar manualmente eventos de mantener el mouse. Por ejemplo, cuando se prueba un Windows Form o una aplicación de Windows Presentation Foundation (WPF), puede haber código personalizado. O podría haber un comportamiento especial definido para mantener el mouse sobre un control, como un nodo de árbol que se expande cuando un usuario mantiene el mouse sobre él. Para probar circunstancias como estas, hay que notificar manualmente al **Generador de pruebas automatizadas de IU** que mantiene el mouse sobre el control presionando las teclas del teclado predefinidas.

Al realizar la prueba de IU codificada, mantenga el mouse sobre el control. Después, mantenga presionadas las teclas **Ctrl**, **Mayús** y **R** del teclado al mismo tiempo. Suelte las teclas. El **Generador de pruebas automatizadas de IU** graba un evento de mantenimiento del mouse.

![IUAutomatizada&#95;MantenerMouse](../test/media/codedui_hover.png)

Después de generar el método de prueba, se agregará al archivo *UIMap.Designer.cs* código similar al del siguiente ejemplo:

```csharp
// Mouse hover '1' label at (87, 9)
Mouse.Hover(uIItem1Text, new Point(87, 9));
```

### <a name="configure-mouse-hover-keyboard-assignments"></a>Configuración de asignaciones de teclado para mantener el mouse

La asignación de teclas para capturar eventos de movimiento del mouse se usa en otra parte del entorno:

Si es necesario, se puede configurar la asignación de teclado predeterminada de **Ctrl**+**Mayús**+**R** que se usa para aplicar eventos de mantenimiento del mouse en las pruebas automatizadas de IU para usar diferentes teclas.

> [!WARNING]
> En circunstancias normales, no tendría que cambiar las asignaciones de teclado para los eventos de mantenimiento del mouse. Tenga cuidado al reasignar la asignación de teclado. Puede que la opción elegida ya esté en uso en otra parte dentro de Visual Studio o de la aplicación que se está probando.

Para cambiar las asignaciones de teclado, modifique el siguiente archivo de configuración:

*%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CodedUITestBuilder.exe.config*

En el archivo de configuración, cambie los valores de las teclas `HoverKeyModifier` y `HoverKey` para modificar las asignaciones de teclado:

```xml
<!-- Begin : Background Recorder Settings -->
<!-- HoverKey to use. -->
<add key="HoverKeyModifier" value="Control, Shift"/>
<add key="HoverKey" value="R"/>
```

### <a name="set-implicit-mouse-hovers-for-the-web-browser"></a>Establecer mantenimientos implícitos del mouse para el explorador web

Si tiene problemas para grabar eventos de mantenimiento del mouse en un sitio web:

En muchos sitios web, cuando se mantiene el mouse sobre un control determinado, este se expande para mostrar detalles adicionales. Normalmente, el aspecto es similar al de los menús de las aplicaciones de escritorio. Dado que este es un patrón común, las pruebas de IU automatizadas permiten el mantenimiento del mouse implícito en la exploración web. Por ejemplo, si registra mantenimientos del mouse en Internet Explorer, se desencadena un evento. Estos eventos pueden provocar registros redundantes de mantenimiento del mouse. Debido a esto, los mantenimientos del mouse implícitos se registran con `ContinueOnError` establecido en `true` en el archivo de configuración de pruebas de IU. Esto permite que la reproducción continúe si un evento de mantener el mouse no se puede realizar.

Para habilitar el registro de mantenimientos implícitos del mouse en un explorador web, abra el archivo de configuración:

*%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CodedUITestBuilder.exe.config*

Compruebe que el archivo de configuración tenga la clave `RecordImplicitiHovers` establecida en el valor `true` como se muestra en el siguiente ejemplo:

```xml
<!--Use this to enable/disable recording of implicit hovers.-->
<add key="RecordImplicitHover" value="true"/>
```

## <a name="customize-the-coded-ui-test"></a>Personalizar la prueba automatizada de IU

Después de crear la prueba de IU codificada, podrá editarla mediante cualquiera de las siguientes herramientas de Visual Studio:

- Use el **generador de pruebas automatizadas de IU** para agregar controles y validación adicionales a las pruebas. Vea la sección [Agregar controles y validar sus propiedades](#validate-the-properties-of-ui-controls) en este tema.

- El **Editor de pruebas automatizadas de IU** permite modificar fácilmente este tipo de pruebas. Con el **Editor de pruebas automatizadas de IU** puede buscar, ver y modificar métodos de prueba. También puede editar acciones de interfaz de usuario y los controles asociados en la asignación de controles de IU. Para obtener más información, vea [Editar pruebas automatizadas de IU con el Editor de pruebas automatizadas de IU](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

- **Editor de código:**

    - Agregue código manualmente para los controles en la prueba, como se describe en la sección para [Propiedades y acciones de control de IU codificada](#coded-ui-control-actions-and-properties) de este tema.

    - Después de crear una prueba de IU codificada, puede modificarla para que esté controlada por datos. Para obtener más información, vea [Crear una prueba automatizada de IU controlada por datos](../test/creating-a-data-driven-coded-ui-test.md).

    - En una reproducción de prueba de UI codificada, puede indicar a la prueba que espere a que se produzcan ciertos eventos, como que se muestre una ventana, que se oculte la barra de progreso, etc. Para ello, agregue el método UITestControl.WaitForControlXXX() adecuado. Para obtener una lista completa de los métodos disponibles, vea [Hacer que las pruebas automatizadas de IU esperen eventos concretos durante la reproducción](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md). Para obtener un ejemplo de una prueba automatizada de UI que espera a que se habilite un control mediante el método WaitForControlEnabled, vea [Tutorial: Crear, editar y mantener una prueba automatizada de IU](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).

    - Las pruebas de IU codificadas proporcionan soporte para algunos de los controles HTML5 incluidos en Internet Explorer 9 o Internet Explorer 10. Para obtener más información, vea [Usar controles HTML5 en pruebas automatizadas de IU](../test/using-html5-controls-in-coded-ui-tests.md).

    - Guía de codificación de pruebas de IU codificadas:

       - [Anatomía de una prueba automatizada de IU](../test/anatomy-of-a-coded-ui-test.md)

       - [Procedimientos recomendados para las pruebas automatizadas de IU](../test/best-practices-for-coded-ui-tests.md)

       - [Probar una aplicación grande con varias asignaciones de IU](../test/testing-a-large-application-with-multiple-ui-maps.md)

       - [Configuraciones y plataformas compatibles con las pruebas automatizadas de IU y las grabaciones de acciones](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)

### <a name="the-generated-code"></a>El código generado

Al elegir **Generar código**, se crean varios elementos de código:

- Una línea en el método de prueba.

    ```csharp
    [CodedUITest]
    public class CodedUITest1
    { ...
      [TestMethod]
      public void CodedUITestMethod1()
      {
          this.UIMap.AddTwoNumbers();
          // To generate more code for this test, select
          // "Generate Code" from the shortcut menu.      }
    }
    ```

     Puede hacer clic con el botón secundario en este método para agregar más acciones y comprobaciones grabadas. También puede editarlo manualmente para ampliar o modificar el código. Por ejemplo, puede incluir parte del código en un bucle.

     También puede agregar nuevos métodos de prueba y agregarles código de la misma forma. Cada método de prueba debe tener el atributo `[TestMethod]`.

- Un método en *UIMap.uitest*.

     Este método incluye los detalles de las acciones grabadas o el valor comprobado. Para editar este código, abra *UIMap.uitest*. Se abre en un editor especializado en el que se pueden eliminar o refactorizar las acciones grabadas.

     También puede ver el método generado en *UIMap.Designer.cs*. Este método realiza las acciones que se grabaron al ejecutar la prueba.

    ```csharp
    // File: UIMap.Designer.cs
    public partial class UIMap
    {
      /// <summary>
      /// Add two numbers
      /// </summary>
      public void AddTwoNumbers()
      { ...   }
    }
    ```

    > [!WARNING]
    > No debe editar este archivo, ya que se volverá a generar al crear más pruebas.

     Puede crear versiones adaptadas de estos métodos copiándolos en *UIMap.cs*. Por ejemplo, puede crear una versión parametrizada a la que pueda llamarse desde un método de prueba:

    ```csharp
    // File: UIMap.cs
    public partial class UIMap // Same partial class
    {
      /// <summary>
      /// Add two numbers - parameterized version
      /// </summary>
      public void AddTwoNumbers(int firstNumber, int secondNumber)
      { ...   // Code modified to use parameters.
      }
    }
    ```

- Declaraciones en *UIMap.uitest*.

    Estas declaraciones representan los controles de IU de la aplicación que usa la prueba. El código generado los usa para hacer funcionar los controles y obtener acceso a sus propiedades.

    También puede usarlos si escribe su propio código. Por ejemplo, puede hacer que el método de prueba elija un hipervínculo en una aplicación web, escribir un valor en un cuadro de texto o crear una bifurcación y realizar diferentes acciones de prueba basadas en el valor de un campo.

    Puede agregar varias pruebas de IU codificadas y varios objetos de asignación de IU y archivos para facilitar la prueba de una aplicación grande. Para obtener más información, vea [Probar una aplicación grande con varios mapas de IU](../test/testing-a-large-application-with-multiple-ui-maps.md).

Para obtener más información sobre el código generado, vea [Anatomía de una prueba automatizada de IU](../test/anatomy-of-a-coded-ui-test.md).

## <a name="coded-ui-control-actions-and-properties"></a>Propiedades y acciones de control de IU codificada

Al usar controles de prueba de IU en pruebas de IU codificadas, se dividen en dos partes: acciones y propiedades.

- La primera parte consta de las acciones que se pueden realizar en los controles de prueba de IU. Por ejemplo, las pruebas de IU codificadas pueden simular clics del mouse en un control de prueba de IU o teclas presionadas en el teclado que van a afectar a un control de prueba de IU.

- La segunda parte consiste en habilitar al usuario para obtener y establecer las propiedades de un control de prueba de IU. Por ejemplo, las pruebas de IU codificadas pueden obtener el número de elementos de un control `ListBox` o establecer el estado de un control `CheckBox` en la opción seleccionada.

**Obtener acceso a las acciones de un control de prueba de IU**

Para realizar acciones en los controles de prueba de IU, como clics del mouse o acciones del teclado, use los métodos de las clases <xref:Microsoft.VisualStudio.TestTools.UITesting.Mouse> y <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard>:

- Para realizar una acción orientada al mouse, como un clic del mouse, en un control de prueba de IU, utilice el método <xref:Microsoft.VisualStudio.TestTools.UITesting.Mouse.Click%2A>.

     `Mouse.Click(buttonCancel);`

- Para realizar una acción orientada al teclado, como escribir en un control de edición, utilice el método <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A>.

     `Keyboard.SendKeys(textBoxDestination, @"C:\Temp\Output.txt");`

**Obtener acceso a las propiedades de un control de prueba de IU**

Para obtener y establecer los valores de propiedad específicos del control de IU, puede obtener o establecer directamente los valores de las propiedades de un control o puede usar los métodos <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A?displayProperty=fullName> y <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A?displayProperty=fullName> con el nombre de la propiedad específica que desea obtener o establecer.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A> devuelve un objeto que puede a su vez convertirse en el objeto <xref:System.Type> apropiado. <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A> acepta un objeto para el valor de la propiedad.

### <a name="to-get-or-set-properties-from-ui-test-controls-directly"></a>Para obtener o establecer las propiedades directamente desde los controles de prueba de IU

Con controles que derivan de <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl>, como [HtmlList](xref:Microsoft.VisualStudio.TestTools.UITesting.HtmlControls.HtmlList) o [WinComboBox](xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinComboBox), puede obtener o establecer directamente sus valores de propiedad. En el código siguiente se muestran algunos ejemplos:

 ```csharp
 int i = myHtmlList.ItemCount;
 myWinCheckBox.Checked = true;
 ```

### <a name="to-get-properties-from-ui-test-controls"></a>Para obtener las propiedades de los controles de prueba de IU

- Para obtener un valor de propiedad de un control, use el método <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>.

- Para especificar la propiedad del control que se va a obtener, use la cadena adecuada de la clase `PropertyNames` en cada control como parámetro de <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>.

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A> devuelve el tipo de datos adecuado, pero este valor devuelto se convierte en <xref:System.Object>. A continuación, el elemento <xref:System.Object> devuelto debe convertirse en el tipo apropiado.

     Ejemplo:

     `int i = (int)GetProperty(myHtmlList.PropertyNames.ItemCount);`

### <a name="to-set-properties-for-ui-test-controls"></a>Para establecer las propiedades de los controles de prueba de IU

- Para establecer una propiedad de un control, utilice el método <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A>.

- Para especificar la propiedad del control que se va a establecer, use la cadena adecuada de la clase `PropertyNames` en cada control como primer parámetro de <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A> y el valor de propiedad como segundo parámetro.

     Ejemplo:

     `SetProperty(myWinCheckBox.PropertyNames.Checked, true);`

## <a name="debug"></a>Depuración

Puede analizar pruebas de IU codificadas mediante los registros de dichas pruebas. Los registros de pruebas de IU codificadas filtran y guardan información importante sobre las series de pruebas de IU codificadas. El formato de los registros permite depurar los problemas rápidamente. Para obtener más información, vea [Análisis de pruebas automatizadas de IU mediante los registros de pruebas automatizadas de IU](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md).

## <a name="whats-next"></a>Pasos adicionales

**Opciones adicionales para ejecutar pruebas de IU codificadas:** Puede ejecutar pruebas de IU codificadas directamente desde Visual Studio, como ya se describió anteriormente en este tema. Además, puede ejecutar pruebas automatizadas de UI desde Microsoft Test Manager o mediante Azure Pipelines. Cuando las pruebas de IU codificadas se automatizan, tienen que interactuar con el escritorio durante su ejecución, a diferencia de otras pruebas automatizadas.

- [Ejecutar pruebas unitarias con el Explorador de pruebas](../test/run-unit-tests-with-test-explorer.md)

- [Ejecutar pruebas en el proceso de compilación](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts)

- [Cómo: Configurar el agente de pruebas para ejecutar pruebas que interactúen con el escritorio](https://msdn.microsoft.com/Library/3a94dd07-6d17-402c-ae8f-7947143755c9)

**Agregar compatibilidad con controles personalizados:**  el marco de pruebas de IU codificadas no admite todas las IU posibles (puede que no sea compatible con la interfaz de usuario que quiera probar). Por ejemplo, no puede crear inmediatamente una prueba automatizada de IU de la interfaz de usuario para Microsoft Excel. Sin embargo, puede crear una extensión al marco de pruebas de IU codificadas que admitirá un control personalizado.

- [Habilitación de pruebas automatizadas de IU en los controles](../test/enable-coded-ui-testing-of-your-controls.md)

- [Extender las pruebas automatizadas de IU y las grabaciones de acciones](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)

Las pruebas de IU codificadas se suelen usar para automatizar las pruebas manuales. Para obtener más información sobre las pruebas manuales, vea [Run manual tests with Microsoft Test Manager](/azure/devops/test/mtm/run-manual-tests-with-microsoft-test-manager?view=vsts) (Ejecución de pruebas manuales con Microsoft Test Manager). Para obtener más información sobre las pruebas automatizadas, vea [Herramientas de prueba de Visual Studio](../test/improve-code-quality.md).

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>
- [Tutorial: Crear, editar y mantener una prueba automatizada de IU](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
- [Crear una prueba automatizada de IU para probar una aplicación para UWP](test-uwp-app-with-coded-ui-test.md)
- [Anatomía de una prueba automatizada de IU](../test/anatomy-of-a-coded-ui-test.md)
- [Procedimientos recomendados para las pruebas automatizadas de IU](../test/best-practices-for-coded-ui-tests.md)
- [Probar una aplicación grande con varias asignaciones de IU](../test/testing-a-large-application-with-multiple-ui-maps.md)
