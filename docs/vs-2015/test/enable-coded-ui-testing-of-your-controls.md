---
title: Habilitar pruebas automatizadas de IU en los controles | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 5ef1188f-89dc-413d-801d-0efdaf9b0427
caps.latest.revision: 24
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c97ee2d05609ee6802da3503e9f514fdc07a4b85
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68871657"
---
# <a name="enable-coded-ui-testing-of-your-controls"></a>Habilitar pruebas de IU codificadas en los controles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para probar los controles con mayor facilidad, implemente compatibilidad con el marco de pruebas de IU codificadas. Se pueden agregar niveles de compatibilidad de forma incremental. Para comenzar, pueden admitirse la grabación, la reproducción y la validación de propiedades. Puede basarse en ello para permitir que el generador de pruebas de IU codificadas reconozca las propiedades personalizadas del control y proporcione clases personalizadas para obtener acceso a esas propiedades desde el código generado. También se puede ayudar al generador de pruebas de IU codificadas a capturar acciones de una manera que es próxima a la intención de la acción que se está registrando.

 **En este tema:**

1. [Admitir la grabación, la reproducción y la validación de propiedades al implementar la accesibilidad](../test/enable-coded-ui-testing-of-your-controls.md#recordandplayback)

2. [Admitir la validación de propiedades personalizada al implementar un proveedor de propiedades](../test/enable-coded-ui-testing-of-your-controls.md#customproprties)

3. [Admitir la generación de código al implementar una clase para obtener acceso a propiedades personalizadas](../test/enable-coded-ui-testing-of-your-controls.md#codegeneration)

4. [Admitir acciones intencionales al implementar un filtro de acción](../test/enable-coded-ui-testing-of-your-controls.md#intentawareactions)

   ![CUIT&#95;Full](../test/media/cuit-full.png "CUIT_Full")

## <a name="recordandplayback"></a> Admitir la grabación, la reproducción y la validación de propiedades al implementar la accesibilidad
 El generador de pruebas de IU codificadas captura información acerca de los controles que encuentra durante una grabación y después genera código para reproducir esa sesión. Si el control no admite accesibilidad, el generador de pruebas de IU codificadas capturará acciones (como clics del mouse) mediante las coordenadas de pantalla. Cuando la prueba se reproduce, el código generado emitirá esos clics del mouse en las mismas coordenadas de la pantalla. Si el control aparece en un lugar diferente de la pantalla cuando se reproduce la prueba, el código generado no podrá realizar esa acción en el control. Esto puede producir errores si la prueba se reproduce en configuraciones de pantalla diferentes, en entornos distintos o después de haberse realizado cambios en el diseño de la interfaz de usuario.

 ![CUIT&#95;RecordNoSupport](../test/media/cuit-recordnosupport.png "CUIT_RecordNoSupport")

 Sin embargo, si implementa accesibilidad, el generador de pruebas de IU codificadas la usará para capturar información sobre el control cuando registre una prueba y genere código. A continuación, al ejecutar la prueba, el código generado volverá a reproducir esos eventos en el control, aunque esté en alguna otra parte en la interfaz de usuario. Los autores de las pruebas también podrán crean aserciones usando las propiedades básicas del control.

 ![CUIT&#95;Record](../test/media/cuit-record.png "CUIT_Record")

### <a name="to-support-record-and-playback-property-validation-and-navigation-for-a-windows-forms-control"></a>Para admitir la grabación y reproducción, la validación de propiedades y la navegación de un control de Windows Forms
 Implemente la accesibilidad para el control como se indica en el procedimiento siguiente, que se explica en detalle en <xref:System.Windows.Forms.AccessibleObject>.

 ![CUIT&#95;Accessible](../test/media/cuit-accessible.png "CUIT_Accessible")

1. Implemente una clase que se derive de <xref:System.Windows.Forms.Control.ControlAccessibleObject> y reemplace la propiedad <xref:System.Windows.Forms.Control.AccessibilityObject%2A> para devolver un objeto de la clase.

    ```csharp
    public partial class ChartControl : UserControl
    {
        // Overridden to return the custom AccessibleObject for the control.
        protected override AccessibleObject CreateAccessibilityInstance()
        {
            return new ChartControlAccessibleObject(this);
        }

        // Inner class ChartControlAccessibleObject represents accessible information
        // associated with the ChartControl and is used when recording tests.
        public class ChartControlAccessibleObject : ControlAccessibleObject
        {
            ChartControl myControl;
            public ChartControlAccessibleObject(ChartControl ctrl)
                : base(ctrl)
            {
                myControl = ctrl;
            }
        }
    }
    ```

2. Reemplace las propiedades y métodos <xref:System.Windows.Forms.AccessibleObject.Role%2A>, <xref:System.Windows.Forms.AccessibleObject.State%2A>, <xref:System.Windows.Forms.AccessibleObject.GetChild%2A> y <xref:System.Windows.Forms.AccessibleObject.GetChildCount%2A> del objeto accesible.

3. Implemente otro objeto de accesibilidad para el control secundario y reemplace la propiedad <xref:System.Windows.Forms.Control.AccessibilityObject%2A> del control secundario para devolver ese objeto de accesibilidad.

4. Reemplace las propiedades y métodos <xref:System.Windows.Forms.AccessibleObject.Bounds%2A>, <xref:System.Windows.Forms.AccessibleObject.Name%2A>, <xref:System.Windows.Forms.AccessibleObject.Parent%2A>, <xref:System.Windows.Forms.AccessibleObject.Role%2A>, <xref:System.Windows.Forms.AccessibleObject.State%2A>, <xref:System.Windows.Forms.AccessibleObject.Navigate%2A> y <xref:System.Windows.Forms.AccessibleObject.Select%2A> del objeto de accesibilidad del control secundario.

> [!NOTE]
> Este tema comienza con el ejemplo de accesibilidad en <xref:System.Windows.Forms.AccessibleObject> en este procedimiento y, a continuación, se basa en este para los procedimientos restantes. Si desea crear una versión operativa del ejemplo de accesibilidad, cree una aplicación de consola y reemplace el código en Program.cs con el código de ejemplo. Tendrá que agregar referencias a Accesibilidad, System.Drawing y System.Windows.Forms. Debe cambiar **Incrustar tipos de interoperabilidad** para la Accesibilidad a **False** para eliminar una advertencia de compilación. Puede cambiar el tipo de salida del proyecto de **Aplicación de consola** a **Aplicación Windows** de modo que no aparezca una ventana de consola al ejecutar la aplicación.

## <a name="customproprties"></a> Admitir la validación de propiedades personalizada al implementar un proveedor de propiedades
 Una vez que haya implementado la compatibilidad básica para grabar, reproducir y validar propiedades, puede poner las propiedades personalizadas del control a disposición de las pruebas de IU codificadas mediante la implementación de un complemento <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>. Por ejemplo, el procedimiento siguiente crea un proveedor de propiedades que permite que las pruebas de IU codificadas tengan acceso a la propiedad State de los controles secundarios CurveLegend del control chart.

 ![CUIT&#95;CustomProps](../test/media/cuit-customprops.png "CUIT_CustomProps")

### <a name="to-support-custom-property-validation"></a>Para admitir la validación de propiedades personalizada
 ![CUIT&#95;Props](../test/media/cuit-props.png "CUIT_Props")

1. Reemplace la propiedad <xref:System.Windows.Forms.AccessibleObject.Description%2A> del objeto accesible CurveLegend para pasar valores de propiedades enriquecidos en la cadena de descripción, separada de la descripción principal (y de otras, si se implementan varias propiedades) por punto y coma (;).

    ```csharp
    public class CurveLegendAccessibleObject : AccessibleObject
    {
        // add the state property value to the description
        public override string Description
        {
            get
            {
                // Add “;” and the state value to the end
                // of the curve legend’s description
                return "CurveLegend; " + State.ToString();
            }
        }
    }
    ```

2. Cree un paquete de extensión de pruebas de IU para el control creando un proyecto de biblioteca de clases y agregando referencias a Accesibilidad, Microsoft.VisualStudio.TestTools.UITesting, Microsoft.VisualStudio.TestTools.UITest.Common y Microsoft.VisualStudio.TestTools.Extension. Cambie **Incrustar tipos de interoperabilidad** para Accesibilidad a **False**.

3. Agregue una clase de proveedor de propiedades que se derive de <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>.

    ```csharp
    using System;
    using System.Collections.Generic;
    using Accessibility;
    using Microsoft.VisualStudio.TestTools.UITesting;
    using Microsoft.VisualStudio.TestTools.UITest.Extension;
    using Microsoft.VisualStudio.TestTools.UITesting.WinControls;
    using Microsoft.VisualStudio.TestTools.UITest.Common;

    namespace ChartControlExtensionPackage
    {
        public class ChartControlPropertyProvider : UITestPropertyProvider
        {
        }
    }
    ```

4. Implemente el proveedor de propiedades colocando nombres y descriptores de propiedad en un objeto <xref:System.Collections.Generic.Dictionary%602>.

    ```csharp
    // Define a map of property descriptors for CurveLegend
    private static Dictionary<string, UITestPropertyDescriptor> curveLegendPropertiesMap = null;
    private static Dictionary<string, UITestPropertyDescriptor> CurveLegendPropertiesMap
    {
        get
        {
            if (curveLegendPropertiesMap == null)
            {
                UITestPropertyAttributes read =
                    UITestPropertyAttributes.Readable |
                    UITestPropertyAttributes.DoNotGenerateProperties;
                curveLegendPropertiesMap =
                    new Dictionary<string, UITestPropertyDescriptor>
                        (StringComparer.OrdinalIgnoreCase);
                curveLegendPropertiesMap.Add("State",
                    new UITestPropertyDescriptor(typeof(string), read));
            }
            return curveLegendPropertiesMap;
        }
    }

    // return the property descriptor
    public override UITestPropertyDescriptor GetPropertyDescriptor(UITestControl uiTestControl, string propertyName)
    {
        return CurveLegendPropertiesMap[propertyName];
    }

    // return the property names
    public override ICollection<string> GetPropertyNames(UITestControl uiTestControl)
    {
        if (uiTestControl.ControlType.NameEquals("Chart") || uiTestControl.ControlType.NameEquals("Text"))
        {
            // the keys of the property map are the collection of property names
            return CurveLegendPropertiesMap.Keys;
        }

        // this is not my control
        throw new NotSupportedException();
    }

    // Get the property value by parsing the accessible description
    public override object GetPropertyValue(UITestControl uiTestControl, string propertyName)
    {
        if (String.Equals(propertyName, "State", StringComparison.OrdinalIgnoreCase))
        {
            object[] native = uiTestControl.NativeElement as object[];
            IAccessible acc = native[0] as IAccessible;

            string[] descriptionTokens = acc.accDescription.Split(new char[] { ';' });
            return descriptionTokens[1];
        }

        // this is not my control
        throw new NotSupportedException();
    }
    ```

5. Reemplace <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A?displayProperty=fullName> para indicar que el ensamblado proporciona compatibilidad específica del control tanto para el control como para sus elementos secundarios.

    ```csharp
    public override int GetControlSupportLevel(UITestControl uiTestControl)
    {
        // For MSAA, check the control type
        if (string.Equals(uiTestControl.TechnologyName, "MSAA",
            StringComparison.OrdinalIgnoreCase) &&
            (uiTestControl.ControlType == "Chart"||uiTestControl.ControlType == "Text"))
        {
            return (int)ControlSupport.ControlSpecificSupport;
        }

        // This is not my control, so return NoSupport
        return (int)ControlSupport.NoSupport;
    }
    ```

6. Reemplace los métodos abstractos restantes de <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider?displayProperty=fullName>.

    ```csharp
    public override string[] GetPredefinedSearchProperties(Type specializedClass)
    {
        throw new NotImplementedException();
    }

    public override Type GetSpecializedClass(UITestControl uiTestControl)
    {
        throw new NotImplementedException();
    }

    public override Type GetPropertyNamesClassType(UITestControl uiTestControl)
    {
        throw new NotImplementedException();
    }

    public override void SetPropertyValue(UITestControl uiTestControl, string propertyName, object value)
    {
        throw new NotImplementedException();
    }

    public override string GetPropertyForAction(UITestControl uiTestControl, UITestAction action)
    {
        throw new NotImplementedException();
    }

    public override string[] GetPropertyForControlState(UITestControl uiTestControl, ControlStates uiState, out bool[] stateValues)
    {
        throw new NotImplementedException();
    }

    ```

7. Agregue una clase de paquete de extensión que se derive de <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>.

    ```csharp
    using System;
    using Microsoft.VisualStudio.TestTools.UITesting;
    using Microsoft.VisualStudio.TestTools.UITest.Extension;
    using Microsoft.VisualStudio.TestTools.UITest.Common;

    namespace ChartControlExtensionPackage
    {
        internal class ChartControlExtensionPackage : UITestExtensionPackage
        {
        }
    }
    ```

8. Defina el atributo `UITestExtensionPackage` para el ensamblado.

    ```csharp
    [assembly: Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage(
                    "ChartControlExtensionPackage",
                    typeof(ChartControlExtensionPackage.ChartControlExtensionPackage))]
    namespace ChartControlExtensionPackage
    {
       …
    ```

9. En la clase de paquete de extensión, reemplace el método <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A?displayProperty=fullName> para devolver la clase de proveedor de propiedades al solicitarse un proveedor de este tipo.

    ```csharp
    internal class ChartControlExtensionPackage : UITestExtensionPackage
    {
        public override object GetService(Type serviceType)
        {
            if (serviceType == typeof(UITestPropertyProvider))
            {
                if (propertyProvider == null)
                {
                    propertyProvider = new ChartControlPropertyProvider();
                }
                return propertyProvider;
            }
            return null;
        }

        private UITestPropertyProvider propertyProvider = null;
    }
    ```

10. Reemplace los métodos y propiedades abstractos restantes de <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>.

    ```csharp

    public override void Dispose() { }

    public override string PackageDescription
    {
        get { return "Supports coded UI testing of ChartControl"; }
    }

    public override string PackageName
    {
        get { return "ChartControl Test Extension"; }
    }

    public override string PackageVendor
    {
        get { return "Microsoft (sample)"; }
    }

    public override Version PackageVersion
    {
        get { return new Version(1, 0); }
    }

    public override Version VSVersion
    {
        get { return new Version(10, 0); }
    }
    ```

11. Compile los binarios y cópielos en **%ProgramFiles%\Common\Microsoft Shared\VSTT\10.0\UITestExtensionPackages**.

> [!NOTE]
> Este paquete de extensión se aplicará a cualquier control de tipo “Text”. Si está probando varios controles del mismo tipo, tendrá que probarlos por separado y administrar los paquetes de la extensión que se implementan al registrar las pruebas.

## <a name="codegeneration"></a> Admitir la generación de código al implementar una clase para obtener acceso a propiedades personalizadas
 Cuando el generador de pruebas de IU codificadas genera código desde una grabación de sesión, este usa la clase <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl> para obtener acceso a los controles.

```csharp

      UITestControl uIAText = this.UIItemWindow.UIChartControlWindow.UIAText;
Assert.AreEqual(this.AssertMethod3ExpectedValues.UIATextState, uIAText.GetProperty("State").ToString());
```

 Si ha implementado un proveedor de propiedades para proporcionar acceso a las propiedades personalizadas del control, puede agregar una clase especializada que se usa para obtener acceso a esas propiedades para simplificar el código generado.

```csharp

      ControlLegend uIAText = this.UIItemWindow.UIChartControlWindow.UIAText;
Assert.AreEqual(this.AssertMethod3ExpectedValues.UIATextState, uIAText.State);
```

### <a name="to-add-a-specialized-class-to-access-your-control"></a>Para agregar una clase especializada para obtener acceso al control
 ![CUIT&#95;CodeGen](../test/media/cuit-codegen.png "CUIT_CodeGen")

1. Implemente una clase que se derive de <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinControl> y agregue el tipo del control a la colección de propiedades de búsqueda en el constructor.

    ```csharp
    public class CurveLegend:WinControl
    {
       public CurveLegend(UITestControl c) : base(c)
       {
          // The curve legend control is a “text” type of control
          SearchProperties.Add(
             UITestControl.PropertyNames.ControlType, "Text");
       }
    }
    ```

2. Implemente las propiedades personalizadas del control como propiedades de la clase.

    ```csharp
    public virtual string State
    {
        get
        {
            return (string)GetProperty("State");
        }
    }
    ```

3. Reemplace el método <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetSpecializedClass%2A?displayProperty=fullName> del proveedor de propiedades para devolver el tipo de la nueva clase para los controles secundarios CurveLegend.

    ```csharp
    public override Type GetSpecializedClass(UITestControl uiTestControl)
    {
       if (uiTestControl.ControlType.NameEquals("Text"))
       {
          // This is text type of control. For my control,
          // that means it’s a curve legend control.
          return typeof(CurveLegend);
       }

       // this is not a curve legend control
       return null;
    }
    ```

4. Reemplace el método <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetPropertyNamesClassType%2A> del proveedor de propiedades para devolver el tipo del método PropertyNames de la nueva clase.

    ```csharp
    public override Type GetPropertyNamesClassType(UITestControl uiTestControl)
    {
        if (uiTestControl.ControlType.NameEquals("Text"))
        {
          // This is text type of control. For my control,
          // that means it’s a curve legend control.
            return typeof(CurveLegend.PropertyNames);
        }

        // this is not a curve legend control
        return null;
    }
    ```

## <a name="intentawareactions"></a> Admitir acciones intencionales al implementar un filtro de acción
 Cuando Visual Studio registra una prueba, captura cada evento del mouse y del teclado. Sin embargo, en algunos casos, la intención de la acción se puede perder en la serie de eventos del mouse y del teclado. Por ejemplo, si el control admite autocompletar, el mismo conjunto de eventos del mouse y del teclado puede dar lugar a un valor diferente cuando la prueba se reproduce en un entorno distinto. Puede agregar un complemento de filtro de acciones que reemplace la serie de eventos del mouse y del teclado por una sola acción. De esta manera, puede reemplazar la serie de eventos del mouse y del teclado que da lugar a la selección de un valor por una única acción que establece el valor. De esta forma, se protegen las pruebas de IU codificadas de las diferencias de autocompletar de un entorno a otro.

### <a name="to-support-intent-aware-actions"></a>Para admitir acciones intencionales
 ![CUIT&#95;Actions](../test/media/cuit-actions.png "CUIT_Actions")

1. Implemente una clase de filtro de acción que se deriva de [UITestActionFilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110)), invalidando las propiedades [ApplyTimeout](/previous-versions/visualstudio/visual-studio-2012/dd984649%28v%3dvs.110%29), [Category](/previous-versions/visualstudio/visual-studio-2012/dd986905(v=vs.110)), [Enabled](/previous-versions/visualstudio/visual-studio-2012/dd985633(v=vs.110)), [FilterType](/previous-versions/visualstudio/visual-studio-2012/dd778726(v=vs.110)), [Group](/previous-versions/visualstudio/visual-studio-2012/dd779219(v=vs.110)) y [Name](/previous-versions/visualstudio/visual-studio-2012/dd998334(v=vs.110)).

    ```csharp
    internal class MyActionFilter : UITestActionFilter
    {
       // If the user actions we are aggregating exceeds the time allowed,
       // this filter is not applied. (The timeout is configured when the
       // test is run.)
       public override bool ApplyTimeout
       {
          get { return true; }
       }

       // Gets the category of this filter. Categories of filters
       // are applied in priority order.
       public override UITestActionFilterCategory Category
       {
          get { return UITestActionFilterCategory.PostSimpleToCompoundActionConversion; }
       }

       public override bool Enabled
       {
          get { return true; }
       }

       public override UITestActionFilterType FilterType
       {
          // This action filter operates on a single action
          get { return UITestActionFilterType.Unary; }
       }

       // Gets the name of the group to which this filter belongs.
       // A group can be enabled/disabled using configuration file.
       public override string Group
       {
          get { return "ChartControlActionFilters"; }
       }

       // Gets the name of this filter.
       public override string Name
       {
          get { return "Convert Double-Click to Single-Click"; }
       }
    ```

2. Reemplace `UITestActionFilter.ProcessRule`. En este ejemplo se reemplaza una acción de doble clic por una acción de un solo clic.

    ```csharp
    public override bool ProcessRule(IUITestActionStack actionStack)
    {
        if (actionStack.Count > 0)
        {
            MouseAction lastAction = actionStack.Peek() as MouseAction;
            if (lastAction != null)
            {
                if (lastAction.UIElement.ControlTypeName.Equals(
                     ControlType.Text.ToString(),
                     StringComparison.OrdinalIgnoreCase))
                {
                    if(lastAction.ActionType == MouseActionType.DoubleClick)
                    {
                        // Convert to single click
                        lastAction.ActionType = MouseActionType.Click;
                    }
                }
            }
        }
        // Do not stop aggregation
        return false;
    }
    ```

3. Agregue el filtro de acción al método <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> del paquete de extensión.

    ```csharp
    public override object GetService(Type serviceType)
    {
       if (serviceType == typeof(UITestPropertyProvider))
       {
          if (propertyProvider == null)
          {
             propertyProvider = new PropertyProvider();
          }
          return propertyProvider;
       }
       else if (serviceType == typeof(UITestActionFilter))
       {
          if (actionFilter == null)
          {
             actionFilter = new RadGridViewActionFilter();
          }
          return actionFilter;
       }
       return null;
    }
    ```

4. Compile los binarios y cópielos en %ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages.

> [!NOTE]
> El filtro de acción no depende de la implementación de accesibilidad ni del proveedor de propiedades.

## <a name="debug-your-property-provider-or-action-filter"></a>Depurar el proveedor de propiedades o filtro de acción
 Los proveedores de propiedades y filtros de acción se implementan en un paquete de extensión cargado y ejecutado por el generador de pruebas de IU codificadas en un proceso independiente de la aplicación.

#### <a name="to-debug-your-property-provider-or-action-filter"></a>Para depurar el proveedor de propiedades o filtro de acción

1. Compile la versión de depuración del paquete de extensión y copie los archivos .dll y .pdb en %ProgramFiles%\Common Files\Microsoft Shared\VSTT\10.0\UITestExtensionPackages.

2. Ejecute la aplicación (no en el depurador).

3. Ejecute el generador de pruebas de IU codificadas.

     `codedUITestBuilder.exe  /standalone`

4. Asocie el depurador al proceso codedUITestBuilder.

5. Establezca puntos de interrupción en el código.

6. En el generador de pruebas de IU codificadas, cree aserciones para ejecutar el proveedor de propiedades y registre acciones para usar los filtros de acción.

## <a name="external-resources"></a>Recursos externos

### <a name="guidance"></a>Guía
 [Pruebas para la entrega continua con Visual Studio 2012 – capítulo 2: Pruebas unitarias: Probar el interior](http://go.microsoft.com/fwlink/?LinkID=255188)

## <a name="see-also"></a>Vea también

- <xref:System.Windows.Forms.AccessibleObject>
- [Usar Automatización de la interfaz de usuario para probar el código](../test/use-ui-automation-to-test-your-code.md)
