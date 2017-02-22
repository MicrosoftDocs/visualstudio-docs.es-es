---
title: "Habilitar pruebas de IU codificadas en los controles | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5ef1188f-89dc-413d-801d-0efdaf9b0427
caps.latest.revision: 22
caps.handback.revision: 22
ms.author: "mlearned"
manager: "douge"
---
# Habilitar pruebas de IU codificadas en los controles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Para probar los controles con mayor facilidad, implemente compatibilidad con el marco de pruebas de IU codificadas.  Se pueden agregar niveles de compatibilidad de forma incremental.  Para comenzar, pueden admitirse la grabación, la reproducción y la validación de propiedades.  Puede basarse en ello para permitir que el generador de pruebas de IU codificadas reconozca las propiedades personalizadas del control y proporcione clases personalizadas para obtener acceso a esas propiedades desde el código generado.  También se puede ayudar al generador de pruebas de IU codificadas a capturar acciones de una manera que es próxima a la intención de la acción que se está registrando.  
  
 **En este tema:**  
  
1.  [Admitir la grabación, la reproducción y la validación de propiedades al implementar la accesibilidad](../test/enable-coded-ui-testing-of-your-controls.md#recordandplayback)  
  
2.  [Admitir la validación de propiedades personalizada implementando un proveedor de propiedades](../test/enable-coded-ui-testing-of-your-controls.md#customproprties)  
  
3.  [Admitir la generación de código al implementar una clase para obtener acceso a propiedades personalizadas](../test/enable-coded-ui-testing-of-your-controls.md#codegeneration)  
  
4.  [Admitir acciones intencionales al implementar un filtro de acción](../test/enable-coded-ui-testing-of-your-controls.md#intentawareactions)  
  
 ![CUIT&#95;Full](../test/media/cuit_full.png "CUIT\_Full")  
  
##  <a name="recordandplayback"></a> Admitir la grabación, la reproducción y la validación de propiedades al implementar la accesibilidad  
 El generador de pruebas de IU codificadas captura información acerca de los controles que encuentra durante una grabación y después genera código para reproducir esa sesión.  Si el control no admite accesibilidad, el generador de pruebas de IU codificadas capturará acciones \(como clics del mouse\) mediante las coordenadas de pantalla.  Cuando la prueba se reproduce, el código generado emitirá esos clics del mouse en las mismas coordenadas de la pantalla.  Si el control aparece en un lugar diferente de la pantalla cuando se reproduce la prueba, el código generado no podrá realizar esa acción en el control.  Esto puede producir errores si la prueba se reproduce en configuraciones de pantalla diferentes, en entornos distintos o después de haberse realizado cambios en el diseño de la interfaz de usuario.  
  
 ![CUIT&#95;RecordNoSupport](../test/media/cuit_recordnosupport.png "CUIT\_RecordNoSupport")  
  
 Sin embargo, si implementa accesibilidad, el generador de pruebas de IU codificadas la usará para capturar información sobre el control cuando registre una prueba y genere código.  A continuación, al ejecutar la prueba, el código generado volverá a reproducir esos eventos en el control, aunque esté en alguna otra parte en la interfaz de usuario.  Los autores de las pruebas también podrán crean aserciones usando las propiedades básicas del control.  
  
 ![CUIT&#95;Record](../test/media/cuit_record.png "CUIT\_Record")  
  
### Para admitir la grabación y reproducción, la validación de propiedades y la navegación de un control de Windows Forms  
 Implemente la accesibilidad para el control como se indica en el procedimiento siguiente, que se explica en detalle en <xref:System.Windows.Forms.AccessibleObject>.  
  
 ![CUIT&#95;Accessible](../test/media/cuit_accessible.png "CUIT\_Accessible")  
  
1.  Implemente una clase que se derive de <xref:System.Windows.Forms.Control.ControlAccessibleObject> y reemplace la propiedad <xref:System.Windows.Forms.Control.AccessibilityObject%2A> para devolver un objeto de la clase.  
  
    ```c#  
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
  
2.  Reemplace las propiedades y métodos <xref:System.Windows.Forms.AccessibleObject.Role%2A>, <xref:System.Windows.Forms.AccessibleObject.State%2A>, <xref:System.Windows.Forms.AccessibleObject.GetChild%2A> y <xref:System.Windows.Forms.AccessibleObject.GetChildCount%2A> del objeto accesible.  
  
3.  Implemente otro objeto de accesibilidad para el control secundario y reemplace la propiedad <xref:System.Windows.Forms.Control.AccessibilityObject%2A> del control secundario para devolver ese objeto de accesibilidad.  
  
4.  Reemplace las propiedades y métodos <xref:System.Windows.Forms.AccessibleObject.Bounds%2A>, <xref:System.Windows.Forms.AccessibleObject.Name%2A>, <xref:System.Windows.Forms.AccessibleObject.Parent%2A>, <xref:System.Windows.Forms.AccessibleObject.Role%2A>, <xref:System.Windows.Forms.AccessibleObject.State%2A>, <xref:System.Windows.Forms.AccessibleObject.Navigate%2A> y <xref:System.Windows.Forms.AccessibleObject.Select%2A> del objeto de accesibilidad del control secundario.  
  
> [!NOTE]
>  Este tema comienza con el ejemplo de accesibilidad en <xref:System.Windows.Forms.AccessibleObject> en este procedimiento y, a continuación, se basa en este para los procedimientos restantes.  Si desea crear una versión operativa del ejemplo de accesibilidad, cree una aplicación de consola y reemplace el código en Program.cs con el código de ejemplo.  Tendrá que agregar referencias a Accesibilidad, System.Drawing y System.Windows.Forms.  Debe cambiar **Incrustar tipos de interoperabilidad** para la Accesibilidad a False para eliminar una advertencia de compilación.  Puede cambiar el tipo de salida del proyecto de Aplicación de consola a aplicación Windows de modo que no aparezca una ventana de consola al ejecutar la aplicación.  
  
##  <a name="customproprties"></a> Admitir la validación de propiedades personalizada implementando un proveedor de propiedades  
 Una vez que haya implementado la compatibilidad básica para grabar, reproducir y validar propiedades, puede poner las propiedades personalizadas del control a disposición de las pruebas de IU codificadas mediante la implementación de un complemento <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>.  Por ejemplo, el procedimiento siguiente crea un proveedor de propiedades que permite que las pruebas de IU codificadas tengan acceso a la propiedad State de los controles secundarios CurveLegend del control chart.  
  
 ![CUIT&#95;CustomProps](../test/media/cuit_customprops.png "CUIT\_CustomProps")  
  
### Para admitir la validación de propiedades personalizada  
 ![CUIT&#95;Props](../test/media/cuit_props.png "CUIT\_Props")  
  
1.  Reemplace la propiedad <xref:System.Windows.Forms.AccessibleObject.Description%2A> del objeto accesible CurveLegend para pasar valores de propiedades enriquecidos en la cadena de descripción, separada de la descripción principal \(y de otras, si se implementan varias propiedades\) por punto y coma \(;\).  
  
    ```c#  
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
  
2.  Cree un paquete de extensión de pruebas de IU para el control creando un proyecto de biblioteca de clases y agregando referencias a Accesibilidad, Microsoft.VisualStudio.TestTools.UITesting, Microsoft.VisualStudio.TestTools.UITest.Common y Microsoft.VisualStudio.TestTools.Extension.  Cambie **Incrustar tipos de interoperabilidad** para Accesibilidad a False.  
  
3.  Agregue una clase de proveedor de propiedades que se derive de <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>.  
  
    ```c#  
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
  
4.  Implemente el proveedor de propiedades colocando nombres y descriptores de propiedad en un objeto <xref:System.Collections.Generic.Dictionary%602>.  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
5.  Reemplace <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A?displayProperty=fullName> para indicar que el ensamblado proporciona compatibilidad específica del control tanto para el control como para sus elementos secundarios.  
  
<CodeContentPlaceHolder>4</CodeContentPlaceHolder>  
6.  Reemplace los métodos abstractos restantes de <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider?displayProperty=fullName>.  
  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
7.  Agregue una clase de paquete de extensión que se derive de <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>.  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
8.  Defina el atributo `UITestExtensionPackage` para el ensamblado.  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
9. En la clase de paquete de extensión, reemplace el método <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A?displayProperty=fullName> para devolver la clase de proveedor de propiedades al solicitarse un proveedor de este tipo.  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
10. Reemplace los métodos y propiedades abstractos restantes de <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>.  
  
<CodeContentPlaceHolder>9</CodeContentPlaceHolder>  
11. Compile los binarios y cópielos en **%ProgramFiles%\\Common\\Microsoft Shared\\VSTT\\10.0\\UITestExtensionPackages**.  
  
> [!NOTE]
>  Este paquete de extensión se aplicará a cualquier control de tipo “Text”.  Si está probando varios controles del mismo tipo, tendrá que probarlos por separado y administrar los paquetes de la extensión que se implementan al registrar las pruebas.  
  
##  <a name="codegeneration"></a> Admitir la generación de código al implementar una clase para obtener acceso a propiedades personalizadas  
 Cuando el generador de pruebas de IU codificadas genera código desde una grabación de sesión, este usa la clase <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl> para obtener acceso a los controles.  
  
<CodeContentPlaceHolder>10</CodeContentPlaceHolder>  
 Si ha implementado un proveedor de propiedades para proporcionar acceso a las propiedades personalizadas del control, puede agregar una clase especializada que se usa para obtener acceso a esas propiedades para simplificar el código generado.  
  
<CodeContentPlaceHolder>11</CodeContentPlaceHolder>  
### Para agregar una clase especializada para obtener acceso al control  
 ![CUIT&#95;CodeGen](../test/media/cuit_codegen.png "CUIT\_CodeGen")  
  
1.  Implemente una clase que se derive de <xref:Microsoft.VisualStudio.TestTools.UITesting.WinControls.WinControl> y agregue el tipo del control a la colección de propiedades de búsqueda en el constructor.  
  
<CodeContentPlaceHolder>12</CodeContentPlaceHolder>  
2.  Implemente las propiedades personalizadas del control como propiedades de la clase.  
  
<CodeContentPlaceHolder>13</CodeContentPlaceHolder>  
3.  Reemplace el método <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetSpecializedClass%2A?displayProperty=fullName> del proveedor de propiedades para devolver el tipo de la nueva clase para los controles secundarios CurveLegend.  
  
<CodeContentPlaceHolder>14</CodeContentPlaceHolder>  
4.  Reemplace el método <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetPropertyNamesClassType%2A> del proveedor de propiedades para devolver el tipo del método PropertyNames de la nueva clase.  
  
<CodeContentPlaceHolder>15</CodeContentPlaceHolder>  
##  <a name="intentawareactions"></a> Admitir acciones intencionales al implementar un filtro de acción  
 Cuando Visual Studio registra una prueba, captura cada evento del mouse y del teclado.  Sin embargo, en algunos casos, la intención de la acción se puede perder en la serie de eventos del mouse y del teclado.  Por ejemplo, si el control admite autocompletar, el mismo conjunto de eventos del mouse y del teclado puede dar lugar a un valor diferente cuando la prueba se reproduce en un entorno distinto.  Puede agregar un complemento de filtro de acciones que reemplace la serie de eventos del mouse y del teclado por una sola acción.  De esta manera, puede reemplazar la serie de eventos del mouse y del teclado que da lugar a la selección de un valor por una única acción que establece el valor.  De esta forma, se protegen las pruebas de IU codificadas de las diferencias de autocompletar de un entorno a otro.  
  
### Para admitir acciones intencionales  
 ![CUIT&#95;Actions](../test/media/cuit_actions.png "CUIT\_Actions")  
  
1.  Implemente una clase de filtro de acción que se derive de <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>, reemplazando las propiedades <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A> y <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A>.  
  
<CodeContentPlaceHolder>16</CodeContentPlaceHolder>  
2.  Reemplace <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ProcessRule%2A>.  En este ejemplo se reemplaza una acción de doble clic por una acción de un solo clic.  
  
<CodeContentPlaceHolder>17</CodeContentPlaceHolder>  
3.  Agregue el filtro de acción al método <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> del paquete de extensión.  
  
<CodeContentPlaceHolder>18</CodeContentPlaceHolder>  
4.  Compile los binarios y cópielos en %ProgramFiles%\\Common Files\\Microsoft Shared\\VSTT\\10.0\\UITestExtensionPackages.  
  
> [!NOTE]
>  El filtro de acción no depende de la implementación de accesibilidad ni del proveedor de propiedades.  
  
## Depurar el proveedor de propiedades o filtro de acción  
 Los proveedores de propiedades y filtros de acción se implementan en un paquete de extensión cargado y ejecutado por el generador de pruebas de IU codificadas en un proceso independiente de la aplicación.  
  
#### Para depurar el proveedor de propiedades o filtro de acción  
  
1.  Compile la versión de depuración del paquete de extensión y copie los archivos .dll y .pdb en %ProgramFiles%\\Common Files\\Microsoft Shared\\VSTT\\10.0\\UITestExtensionPackages.  
  
2.  Ejecute la aplicación \(no en el depurador\).  
  
3.  Ejecute el generador de pruebas de IU codificadas.  
  
     `codedUITestBuilder.exe  /standalone`  
  
4.  Asocie el depurador al proceso codedUITestBuilder.  
  
5.  Establezca puntos de interrupción en el código.  
  
6.  En el generador de pruebas de IU codificadas, cree aserciones para ejecutar el proveedor de propiedades y registre acciones para usar los filtros de acción.  
  
## Recursos externos  
  
### Guía  
 [Capítulo 2 sobre pruebas unitarias internas en la guía sobre pruebas para entrega continua con Visual Studio 2012](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
## Vea también  
 <xref:System.Windows.Forms.AccessibleObject>   
 [Usar la automatización de IU para probar el código](../test/use-ui-automation-to-test-your-code.md)