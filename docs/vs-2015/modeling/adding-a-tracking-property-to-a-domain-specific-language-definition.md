---
title: Agregar una propiedad de seguimiento a una definición de lenguaje específico de dominio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- tracking properties [Domain-Specific Language Tools], walkthrough
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
ms.assetid: 4aa47777-de75-4897-a423-a3c4426b4125
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 19d673d9d09ce95580e25033966e1a901255fd90
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74292644"
---
# <a name="adding-a-tracking-property-to-a-domain-specific-language-definition"></a>Agregar una propiedad de seguimiento a una definición de lenguaje específico de dominio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tutorial se muestra cómo agregar una propiedad de seguimiento a un modelo de dominio.

 Una propiedad de *dominio de seguimiento* es una propiedad que el usuario puede actualizar, pero que tiene un valor predeterminado que se calcula usando los valores de otras propiedades o elementos de dominio.

 Por ejemplo, en el Herramientas del lenguaje específico de dominio (herramientas de DSL), la propiedad nombre para mostrar de una clase de dominio tiene un valor predeterminado que se calcula con el nombre de la clase de dominio, pero un usuario puede cambiar el valor en tiempo de diseño o restablecerlo en el valor calculado.

 En este tutorial, creará un lenguaje específico de dominio (DSL) que tiene una propiedad de seguimiento de espacio de nombres que tiene un valor predeterminado basado en la propiedad espacio de nombres predeterminado del modelo. Para obtener más información sobre las propiedades de seguimiento, vea [definir propiedades de seguimiento](https://msdn.microsoft.com/0538b0e4-6221-4e7d-911a-b92cd622f0be).

- Las herramientas de DSL admiten los descriptores de propiedad de seguimiento. Sin embargo, no se puede usar el diseñador DSL para agregar una propiedad de seguimiento a un idioma. Por lo tanto, debe agregar código personalizado para definir e implementar la propiedad de seguimiento.

  Una propiedad de seguimiento tiene dos Estados: seguimiento y actualizado por el usuario. Las propiedades de seguimiento tienen las siguientes características:

- Cuando se encuentra en el estado de seguimiento, se calcula el valor de la propiedad de seguimiento y el valor se actualiza a medida que otras propiedades del modelo cambian.

- En el estado actualizado por usuario, el valor de la propiedad de seguimiento conserva el valor en el que el usuario estableció la propiedad por última vez.

- En la ventana **propiedades** , el comando de **restablecimiento** de la propiedad de seguimiento solo está habilitado cuando la propiedad está en el estado actualizado por usuario. El comando **RESET** establece el estado de la propiedad Tracking en Tracking.

- En la ventana **propiedades** , cuando la propiedad Tracking está en el estado Tracking, su valor se muestra en una fuente normal.

- En la ventana **propiedades** , cuando la propiedad Tracking está en el estado de usuario actualizado por, su valor se muestra en negrita.

## <a name="prerequisites"></a>Requisitos previos
 Para poder iniciar este tutorial, primero debe instalar estos componentes:

|||
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185579](https://go.microsoft.com/fwlink/?LinkID=185579)|
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185580](https://go.microsoft.com/fwlink/?LinkID=185580)|
|[!INCLUDE[dsl](../includes/dsl-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185581](https://go.microsoft.com/fwlink/?LinkID=185581)|

## <a name="creating-the-dsl-project"></a>Crear el proyecto DSL
 Cree el proyecto para el lenguaje específico del dominio.

#### <a name="to-create-the-project"></a>Para crear el proyecto

1. Cree un proyecto de Diseñador de lenguaje específico de dominio. Denomínelo `TrackingPropertyDSL`.

2. En el **Asistente para diseñador de lenguaje específico de dominio**, establezca las siguientes opciones:

    1. Seleccione la plantilla **MinimalLanguage** .

    2. Use el nombre predeterminado para el lenguaje específico del dominio, `TrackingPropertyDSL`.

    3. Establezca la extensión de los archivos de modelo en `trackingPropertyDsl`.

    4. Use el icono de plantilla predeterminada para los archivos de modelo.

    5. Establezca el nombre del producto en `Product Name`.

    6. Establezca el nombre de la empresa en `Company Name`.

    7. Use el valor predeterminado del espacio de nombres de la raíz para los proyectos de la solución, `CompanyName.ProductName.TrackingPropertyDSL`.

    8. Permita que el asistente cree un archivo de clave de nombre seguro para los ensamblados.

    9. Revise los detalles de la solución y, a continuación, haga clic en **Finalizar** para crear el proyecto de definición de DSL.

## <a name="customizing-the-default-dsl-definition"></a>Personalización de la definición de DSL predeterminada
 En esta sección, personalizará la definición de DSL para que contenga los siguientes elementos:

- Propiedad de seguimiento del espacio de nombres para cada elemento del modelo.

- Una propiedad IsNamespaceTracking booleana para cada elemento del modelo. Esta propiedad indicará si la propiedad de seguimiento está en el estado de seguimiento o en el estado actualizado por el usuario.

- Propiedad de espacio de nombres predeterminada para el modelo. Esta propiedad se utilizará para calcular el valor predeterminado de la propiedad de seguimiento del espacio de nombres.

- Propiedad calculada CustomElements para el modelo. Esta propiedad indicará la proporción de elementos que tienen un espacio de nombres personalizado.

#### <a name="to-add-the-domain-properties"></a>Para agregar las propiedades de dominio

1. En el diseñador de DSL, haga clic con el botón secundario en la clase de dominio **ExampleModel** , seleccione **Agregar**y, a continuación, haga clic en **DomainProperty**.

    1. Asigne a la nueva propiedad el nombre `DefaultNamespace`.

    2. En la ventana **propiedades** de la nueva propiedad, establezca el **valor predeterminado** en `DefaultNamespace`y el **tipo** en **cadena**.

2. Agregue una propiedad de dominio denominada `CustomElements`a la clase de dominio **ExampleModel** .

     En la ventana **propiedades** de la nueva propiedad, establezca **Kind** en **Calculated**.

3. Agregue una propiedad de dominio denominada `Namespace`a la clase de dominio **ExampleElement** .

     En la ventana **propiedades** de la nueva propiedad, establezca **en explorable** como **false**y establezca **Kind** en **CustomStorage**.

4. Agregue una propiedad de dominio denominada `IsNamespaceTracking`a la clase de dominio **ExampleElement** .

     En la ventana **propiedades** de la nueva propiedad, establezca **es explorable** en **false**, establezca el **valor predeterminado** en `true`y establezca **tipo** en **booleano**.

#### <a name="to-update-the-diagram-elements-and-dsl-details"></a>Para actualizar los elementos de diagrama y los detalles de DSL

1. En el diseñador DSL, haga clic con el botón secundario en la forma geometría **ExampleShape** , seleccione **Agregar**y, a continuación, haga clic en **Decorator de texto**.

    1. Asigne al nuevo texto el nombre `NamespaceDecorator`.

    2. En la ventana **propiedades** del decorador de texto, establezca **posición** en **InnerBottomLeft**.

2. En el diseñador de DSL, seleccione la línea que conecta la clase **ExampleElement** con la forma **ExampleShape** .

    1. En la ventana **detalles de DSL** , seleccione la pestaña asignaciones de elemento **Decorator** .

    2. En la lista **decoradores** , seleccione **NamespaceDecorator**, seleccione su casilla y, en la lista de **propiedades de pantalla** , seleccione espacio de **nombres**.

3. En el **Explorador de DSL**, expanda la carpeta clases de **dominio** , haga clic con el botón secundario en el nodo **ExampleElement** y, a continuación, haga clic en **Agregar nuevo descriptor de tipo de dominio**.

    1. Expanda el nodo **ExampleElement** y seleccione el nodo **descriptor de tipo personalizado (descriptor de tipo de dominio)** .

    2. En la ventana **propiedades** del descriptor de tipos de dominio, establezca **código personalizado** en **true**.

4. En el **Explorador de DSL**, seleccione el nodo comportamiento de **serialización XML** .

    1. En la ventana **propiedades** , establezca **Custom post upload** en **true**.

## <a name="transforming-templates"></a>Transformar plantillas
 Ahora que ha definido las clases de dominio y las propiedades del DSL, puede comprobar que la definición de DSL se puede transformar correctamente para regenerar el código del proyecto.

#### <a name="to-transform-the-text-templates"></a>Para transformar las plantillas de texto

1. En la barra de herramientas **Explorador de soluciones** , haga clic en **transformar todas las plantillas**.

2. El sistema vuelve a generar el código de la solución y guarda DslDefinition. DSL. Para obtener información sobre el formato XML de los archivos de definición, vea [el archivo DslDefinition. DSL](../modeling/the-dsldefinition-dsl-file.md).

## <a name="creating-files-for-custom-code"></a>Crear archivos para código personalizado
 Al transformar todas las plantillas, el sistema genera el código fuente que define el lenguaje específico del dominio en los proyectos DSL y DslPackage. Para que pueda evitar interferir con el texto generado, escriba el código personalizado en archivos que sean distintos de los archivos de código generados.

 Debe proporcionar código para mantener el valor y el estado de la propiedad de seguimiento. Para ayudarle a distinguir el código personalizado del código generado y para evitar conflictos de nombres de archivo, coloque los archivos de código personalizado en una subcarpeta independiente.

#### <a name="to-create-the-code-files"></a>Para crear los archivos de código

1. En **Explorador de soluciones**, haga clic con el botón secundario en el proyecto **DSL** , elija **Agregar**y, a continuación, haga clic en **nueva carpeta**. Asigne a la nueva carpeta el nombre `CustomCode`.

2. Haga clic con el botón secundario en la nueva carpeta **CustomCode** , seleccione **Agregar**y, a continuación, haga clic en **nuevo elemento**.

3. Seleccione la plantilla de **archivo de código** , establezca el **nombre** en `NamespaceTrackingProperty.cs`y, a continuación, haga clic en **Aceptar**.

     El archivo NamespaceTrackingProperty.cs se crea y se abre para su edición.

4. En la carpeta, cree los archivos de código siguientes: `ExampleModel.cs,``HelperClasses.cs`, `Serialization.cs`y `TypeDescriptor.cs`.

5. En el proyecto **DslPackage** , cree también una carpeta `CustomCode` y agréguele un archivo de código `Package.cs`.

## <a name="adding-helper-classes-to-support-tracking-properties"></a>Agregar clases auxiliares para admitir propiedades de seguimiento
 En el archivo HelperClasses.cs, agregue las clases `TrackingHelper` y `CriticalException` como se indica a continuación. Hará referencia a estas clases más adelante en este tutorial.

#### <a name="to-add-the-helper-classes"></a>Para agregar las clases auxiliares

1. Agregue el código siguiente al archivo HelperClasses.cs.

    ```csharp
    using System;
    using System.Collections;
    using System.Diagnostics;
    using Microsoft.VisualStudio.Modeling;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        internal static class TrackingHelper
        {
            /// <summary>Notify each model element in a collection that a tracked
            /// property has changed.</summary>
            /// <param name="store">The store for the model.</param>
            /// <param name="collection">The collection of model elements that
            /// contain the tracking property.</param>
            /// <param name="propertyId">The ID of the tracking property.</param>
            /// <param name="trackingPropertyId">The ID of the property that
            /// indicates whether the tracking property is tracking.</param>
            internal static void UpdateTrackingCollectionProperty(
                Store store,
                IEnumerable collection,
                Guid propertyId,
                Guid trackingPropertyId)
            {
                DomainPropertyInfo propInfo =
                    store.DomainDataDirectory.GetDomainProperty(propertyId);

                DomainPropertyInfo trackingPropInfo =
                    store.DomainDataDirectory.GetDomainProperty(trackingPropertyId);

                Debug.Assert(propInfo != null);
                Debug.Assert(trackingPropInfo != null);
                Debug.Assert(trackingPropInfo.PropertyType.Equals(typeof(bool)),
                    "Tracking property not specified as a boolean");

                foreach (ModelElement element in collection)
                {
                    // If the tracking property is currently tracking, then notify
                    // it that the tracked property has changed.
                    bool isTracking = (bool)trackingPropInfo.GetValue(element);
                    if (isTracking)
                    {
                        propInfo.NotifyValueChange(element);
                    }
                }
            }
        }

        /// <summary>Helper class to flag critical exceptions from ones that are
        /// safe to ignore.</summary>
        internal static class CriticalException
        {
            /// <summary>Gets whether an exception is critical and can not be
            /// ignored.</summary>
            /// <param name="ex">The exception to check.</param>
            /// <returns>True if the exception is critical.</returns>
            internal static bool IsCriticalException(Exception ex)
            {
                if (ex is NullReferenceException
                    || ex is StackOverflowException
                    || ex is OutOfMemoryException
                    || ex is System.Threading.ThreadAbortException)
                    return true;

                if (ex.InnerException != null)
                    return IsCriticalException(ex.InnerException);

                return false;
            }
        }
    }
    ```

## <a name="adding-custom-code-for-the-custom-type-descriptor"></a>Agregar código personalizado para el descriptor de tipos personalizado
 Implemente el método `GetCustomProperties` para el descriptor de tipo de la clase de dominio `ExampleModel`.

> [!NOTE]
> El código generado por las herramientas de DSL para el descriptor de tipos personalizado para `ExampleModel` llama a `GetCustomProperties`; sin embargo, las herramientas de DSL no generan código que implementa el método.

 La definición de este método crea el descriptor de la propiedad de seguimiento para la propiedad de seguimiento del espacio de nombres. Además, proporcionar atributos para la propiedad Tracking permite que la ventana **propiedades** muestre correctamente la propiedad.

#### <a name="to-modify-the-type-descriptor-for-the-examplemodel-domain-class"></a>Para modificar el descriptor de tipos para la clase de dominio ExampleModel

1. Agregue el código siguiente al archivo TypeDescriptor.cs.

    ```csharp
    using System;
    using System.ComponentModel;
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Design;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        // To the custom type descriptor for the ExampleElement domain class, add
        // the GetCustomProperties method.
        public partial class ExampleElementTypeDescriptor
        {
            /// <summary>Returns the property descriptors for the described
            /// ExampleElement domain class.</summary>
            /// <remarks>This method adds the tracking property descriptor.
            /// </remarks>
            private PropertyDescriptorCollection GetCustomProperties(
                Attribute[] attributes)
            {
                // Get the default property descriptors from the base class
                PropertyDescriptorCollection propertyDescriptors =
                    base.GetProperties(attributes);

                // Get a reference to the model element that is being described.
                ExampleElement source = this.ModelElement as ExampleElement;

                //Add the descriptor for the tracking property.
                if (source != null)
                {
                    DomainPropertyInfo domainProperty =
                        source.Store.DomainDataDirectory.GetDomainProperty(
                            ExampleElement.NamespaceDomainPropertyId);

                    DomainPropertyInfo trackingProperty =
                        source.Store.DomainDataDirectory.GetDomainProperty(
                            ExampleElement.IsNamespaceTrackingDomainPropertyId);

                    // Define attributes for the tracking property so that the
                    // Properties window displays the property correctly.
                    Attribute[] attr = new Attribute[] {
                        new DisplayNameAttribute("Element Namespace"),
                        new DescriptionAttribute("The namespace of the element."),
                        new CategoryAttribute("Tracking Properties"),
                    };

                    propertyDescriptors.Add(new TrackingPropertyDescriptor(
                        source, domainProperty, trackingProperty, attr));
                }

                // Return the property descriptors for this element
                return propertyDescriptors;
            }
        }
    }
    ```

## <a name="adding-custom-code-for-the-package"></a>Agregar código personalizado para el paquete
 El código generado define un proveedor de descripción de tipos para la clase de dominio ExampleElement; sin embargo, debe agregar código para indicar a la DSL que use este proveedor de descripción de tipos.

#### <a name="to-update-the-dsl-package-to-use-your-custom-type-descriptor"></a>Para actualizar el paquete DSL para usar el descriptor de tipos personalizado

1. Agregue el código siguiente al archivo Package.cs.

    ```csharp
    using System.ComponentModel;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        // Override the default Initialize method.
        internal sealed partial class TrackingPropertyDSLPackage
        {
            protected override void Initialize()
            {
                // Add the custom type descriptor for the ExampleElement type.
                TypeDescriptor.AddProvider(
                    new ExampleElementTypeDescriptionProvider(),
                    typeof(ExampleElement));

                base.Initialize();
            }
        }
    }
    ```

## <a name="adding-custom-code-for-the-model"></a>Agregar código personalizado para el modelo
 Implemente el método `GetCustomElementsValue` para la clase de dominio `ExampleModel`.

> [!NOTE]
> El código generado por las herramientas de DSL para `ExampleModel` llama `GetCustomElementsValue`; sin embargo, las herramientas de DSL no generan código que implementa el método.

 La definición del método `GetCustomElementsValue` proporciona la lógica para la propiedad calculada CustomElements de `ExampleModel`. Este método cuenta el número de clases de dominio `ExampleElement` que tienen una propiedad de seguimiento de espacio de nombres que tiene un valor actualizado por el usuario y devuelve una cadena que representa este recuento como una proporción del total de elementos del modelo.

 Además, agregue un método `OnDefaultNamespaceChanged` a `ExampleModel`e invalide el método `OnValueChanged` de la `DefaultNamespacePropertyHandler` clase anidada de `ExampleModel` para llamar a `OnDefaultNamespaceChanged`.

 Dado que la propiedad DefaultNamespace se usa para calcular la propiedad de seguimiento del espacio de nombres, `ExampleModel` debe notificar a todas `ExampleElement` clases de dominio que el valor de DefaultNamespace haya cambiado.

#### <a name="to-modify-the-property-handler-for-the-tracked-property"></a>Para modificar el controlador de propiedad de la propiedad sometida a seguimiento

1. Agregue el código siguiente al archivo ExampleModel.cs.

    ```csharp
    using System.Linq;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        public partial class ExampleModel
        {
            public string GetCustomElementsValue()
            {
                if (this.Elements.Count == 0) return "0/0";

                int number = this.Elements.Count(e => !e.IsNamespaceTracking);
                return string.Format("{0}/{1}", number, this.Elements.Count);
            }

            #region Value changed handler for the tracked property

            // When a tracked property changes, it needs to notify all of the properties
            // that track it.

            /// <summary>Called by the DefaultNamespace property value handler when the
            /// DefaultNamespace property changes.</summary>
            /// <param name="oldValue">The previous value of the property.</param>
            /// <param name="newValue">The new value of the property.</param>
            protected virtual void OnDefaultNamespaceChanged(
                string oldValue, string newValue)
            {
                // Use the helper class to notify all of the elements in the model
                // that the default namespace has changed.
                TrackingHelper.UpdateTrackingCollectionProperty(
                    this.Store,
                    this.Elements,
                    ExampleElement.NamespaceDomainPropertyId,
                    ExampleElement.IsNamespaceTrackingDomainPropertyId);
            }

            // Update the change handler for the DefaultNamespace property.
            internal sealed partial class DefaultNamespacePropertyHandler
            {
                /// <summary>Called when the DefaultNamespace property changes.</summary>
                /// <param name="element">The model element that has the property that
                /// changed.</param>
                /// <param name="oldValue">The previous value of the property.</param>
                /// <param name="newValue">The new value of the property.</param>
                protected override void OnValueChanged(
                    ExampleModel element, string oldValue, string newValue)
                {
                    base.OnValueChanged(element, oldValue, newValue);

                    if (!element.Store.InUndoRedoOrRollback)
                    {
                        element.OnDefaultNamespaceChanged(oldValue, newValue);
                    }
                }
            }

            #endregion
        }
    }
    ```

## <a name="adding-custom-code-for-the-tracking-property"></a>Agregar código personalizado para la propiedad Tracking
 Agregue un método `CalculateNamespace` a la clase de dominio `ExampleElement`.

 La definición de este método proporciona la lógica para la propiedad calculada CustomElements de `ExampleModel`. Este método cuenta el número de clases de dominio `ExampleElement` que tienen una propiedad de seguimiento del espacio de nombres que se encuentra en el estado actualizado por el usuario y devuelve una cadena que representa este recuento como una proporción del total de elementos del modelo.

 Además, agregue almacenamiento para y métodos que se van a obtener y establecer, la propiedad de almacenamiento personalizado del espacio de nombres de la clase de dominio `ExampleElement`.

> [!NOTE]
> El código generado por las herramientas de DSL para `ExampleModel` llama a los métodos GET y set; sin embargo, las herramientas de DSL no generan código que implemente los métodos.

#### <a name="to-add-the-method-for-the-custom-type-descriptor"></a>Para agregar el método para el descriptor de tipos personalizado

1. Agregue el código siguiente al archivo NamespaceTrackingProperty.cs.

    ```csharp
    using System;
    using Microsoft.VisualStudio.Modeling;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        // To the domain class that has the tracking property, add the caluclation
        // for when the property is tracking.
        public partial class ExampleElement
        {
            /// <summary>Calculates the actual value of the property when it is
            /// tracking.</summary>
            /// <returns>The value of the tracking property when it is
            /// tracking.</returns>
            /// <remarks>Making this method virtual allows child classes to modify
            /// the calculation. This method does not need to perform validation, as
            /// its caller handles validation prior to calling this method.
            /// <para>In this case, the tracking value depends on the default namespace
            /// property of the parent model.</para></remarks>
            protected virtual string CalculateNamespace()
            {
                return this.ExampleModel.DefaultNamespace;
            }

            #region Tracking property implementation

            // Implement the Namespace domain property of the ExampleElement domain class,
            // and update the IsNamespaceTracking domain property value handler.

            /// <summary>Storage for the Namespace property.</summary>
            private string namespaceStorage;

            /// <summary>Gets the value of the Namespace property.</summary>
            /// <returns>The value of the Namespace property.</returns>
            private string GetNamespaceValue()
            {
                // Only retrieve the tracked value if the store is not in the
                // middle of a serialization transaction.
                bool loading = this.Store.TransactionManager.InTransaction
                    && this.Store.TransactionManager.CurrentTransaction.IsSerializing;

                if (!loading && this.IsNamespaceTracking)
                {
                    try
                    {
                        return this.CalculateNamespace();
                    }
                    catch (NullReferenceException)
                    {
                        return default(string);
                    }
                    catch (Exception e)
                    {
                        if (CriticalException.IsCriticalException(e))
                        {
                            throw;
                        }
                        else
                        {
                            return default(string);
                        }
                    }
                }

                return namespaceStorage;
            }

            /// <summary>Sets the value of the Namespace property.</summary>
            /// <param name="value">The new value for the property.</param>
            private void SetNamespaceValue(string value)
            {
                namespaceStorage = value;

                // Only update the state of the tracking property if the store is
                // not in the middle of a serialization transaction.
                bool loading = this.Store.TransactionManager.InTransaction
                    && this.Store.TransactionManager.CurrentTransaction.IsSerializing;

                if (!this.Store.InUndoRedoOrRollback && !loading)
                {
                    this.IsNamespaceTracking = false;
                }
            }

            // Update the default behavior of the ExampleElement.IsNamespaceTracking
            // domain property value handler.
            internal sealed partial class IsNamespaceTrackingPropertyHandler
            {
                /// <summary>Called after the IsNamespaceTracking property changes.
                /// </summary>
                /// <param name="element">The model element that has the property
                /// that changed.</param>
                /// <param name="oldValue">The previous value of the property.
                /// </param>
                /// <param name="newValue">The new value of the property.</param>
                protected override void OnValueChanged(
                    ExampleElement element, Boolean oldValue, Boolean newValue)
                {
                    base.OnValueChanged(element, oldValue, newValue);
                    if (!element.Store.InUndoRedoOrRollback && newValue)
                    {
                        DomainPropertyInfo propInfo =
                            element.Store.DomainDataDirectory.GetDomainProperty(
                                ExampleElement.NamespaceDomainPropertyId);
                        propInfo.NotifyValueChange(element);
                    }
                }

                /// <summary>Performs the reset operation for the IsNamespaceTracking
                /// property for a model element.</summary>
                /// <param name="element">The model element that has the property
                /// to reset.</param>
                internal void ResetValue(ExampleElement element)
                {
                    object calculatedValue = null;

                    try
                    {
                        calculatedValue = element.CalculateNamespace();
                    }
                    catch (NullReferenceException)
                    {
                    }
                    catch (System.Exception e)
                    {
                        if (CriticalException.IsCriticalException(e))
                        {
                            throw;
                        }
                    }

                    if ((calculatedValue != null
                        && object.Equals(element.Namespace, calculatedValue)))
                    {
                        element.isNamespaceTrackingPropertyStorage = true;
                    }
                }

                /// <summary>Method to set IsNamespaceTracking to false so that this
                /// instance of this tracking property is not storage-based.
                /// </summary>
                /// <param name="element">The element on which to reset the property
                /// value.</param>
                internal void PreResetValue(ExampleElement element)
                {
                    // Force the IsNamespaceTracking property to false so that the value
                    // of the Namespace property is retrieved from storage.
                    element.isNamespaceTrackingPropertyStorage = false;
                }
            }

            #endregion
        }
    }
    ```

## <a name="adding-custom-code-to-support-serialization"></a>Agregar código personalizado para admitir la serialización
 Agregue código para admitir el comportamiento posterior a la carga personalizada para la serialización XML.

> [!NOTE]
> El código generado por las herramientas de DSL llama a los métodos `OnPostLoadModel` y `OnPostLoadModelAndDiagram`; sin embargo, las herramientas de DSL no generan código que implementa estos métodos.

#### <a name="to-add-code-to-support-the-custom-post-load-behavior"></a>Para agregar código para admitir el comportamiento posterior a la carga personalizada

1. Agregue el código siguiente al archivo Serialization.cs.

    ```csharp
    using System;
    using System.Diagnostics;
    using Microsoft.VisualStudio.Modeling;

    namespace CompanyName.ProductName.TrackingPropertyDSL
    {
        #region Helper classes for maintaining state while the store is serializing.

        public abstract partial class TrackingPropertyDSLSerializationHelperBase
        {
            /// <summary>Reset the tracking state properties to their natural values
            /// based on comparing storage with calculation.</summary>
            /// <param name="store">The store that contains this model.</param>
            internal static void ResetTrackingProperties(Store store)
            {
                // Two passes required - one to set all elements to storage-based
                // then another to set some back to being tracking.
                foreach (ModelElement element in store.ElementDirectory.AllElements)
                {
                    ExampleElement myElementInstance = element as ExampleElement;
                    if (myElementInstance != null)
                    {
                        myElementInstance.PreResetIsTrackingProperties();
                        continue;
                    }
                }
                foreach (ModelElement element in store.ElementDirectory.AllElements)
                {
                    ExampleElement myElementInstance = element as ExampleElement;
                    if (myElementInstance != null)
                    {
                        myElementInstance.ResetIsTrackingProperties();
                        continue;
                    }
                }
            }
        }

        // Add the pre-reset and reset methods for the model element.
        public partial class ExampleElement
        {
            /// <summary>Calls the pre-reset method on the associated property value
            /// handler for each tracking property of this model element.</summary>
            internal virtual void PreResetIsTrackingProperties()
            {
                ExampleElement.IsNamespaceTrackingPropertyHandler.Instance.PreResetValue(this);
            }

            /// <summary>Calls the reset method on the associated property value
            /// handler for each tracking property of this model element.</summary>
            internal virtual void ResetIsTrackingProperties()
            {
                ExampleElement.IsNamespaceTrackingPropertyHandler.Instance.ResetValue(this);
            }
        }

        #endregion

        #region Custom serialization code

        // To the serialization helper for the TrackingPropertyDSL class, add post
        // load handlers to bind the tracking property to the serialization process.
        // These handlers manage the tracking states and property values when the
        // model is serialized and deserialized.
        public partial class TrackingPropertyDSLSerializationHelperBase
        {
            /// <summary>Customize model loading.</summary>
            /// <param name="serializationResult">The serialization result from the
            /// load operation.</param>
            /// <param name="partition">The partition in which the new
            /// instance was created.</param>
            /// <param name="fileName">The name of the file from which the
            /// instance was deserialized.</param>
            /// <param name="modelRoot">The root of the file that was loaded.
            /// </param>
            private void OnPostLoadModel(
                SerializationResult serializationResult,
                Partition partition,
                string fileName,
                ExampleModel modelRoot)
            {
            }

            /// <summary>Customize model and diagram loading.</summary>
            /// <param name="serializationResult">Stores serialization result from
            /// the load operation.</param>
            /// <param name="modelPartition">Partition in which the new
            /// instance will be created.</param>
            /// <param name="modelFileName">Name of the file from which the
            /// instance will be deserialized.</param>
            /// <param name="diagramPartition">Partition in which the new
            /// diagram instance will be created.</param>
            /// <param name="diagramFileName">Name of the file from which the
            /// diagram instance will be deserialized.</param>
            /// <param name="modelRoot">The root of the file that was loaded.</param>
            /// <param name="diagram">The diagram matching the modelRoot.</param>
            private void OnPostLoadModelAndDiagram(
                SerializationResult serializationResult,
                Partition modelPartition,
                string modelFileName,
                Partition diagramPartition,
                string diagramFileName,
                ExampleModel modelRoot,
                TrackingPropertyDSLDiagram diagram)
            {
                Debug.Assert(modelPartition != null);
                Debug.Assert(modelPartition.Store != null);

                // Tracking properties need to be set up according to whether the
                // serialization matches the calculated values.
                TrackingPropertyDSLSerializationHelperBase.ResetTrackingProperties(
                    modelPartition.Store);
            }
        }

        #endregion
    }
    ```

## <a name="testing-the-language"></a>Probar el idioma
 El paso siguiente consiste en compilar y ejecutar el diseñador de DSL en una nueva instancia de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] para que pueda comprobar que la propiedad de seguimiento funciona correctamente.

#### <a name="to-exercise-the-language"></a>Para probar el lenguaje

1. En el menú **Compilar**, haga clic en **Recompilar solución**.

2. En el menú **Depurar**, haga clic en **Iniciar depuración**.

     La compilación experimental de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] abre la solución de **depuración** , que contiene un archivo de prueba vacío.

3. En **Explorador de soluciones**, haga doble clic en el archivo test. trackingPropertyDsl para abrirlo en el diseñador y, a continuación, haga clic en la superficie de diseño.

     Observe que en la ventana **propiedades** del diagrama, la propiedad **espacio de nombres predeterminado** es **DefaultNamespace**y la propiedad **elementos personalizados** es **0/0**.

4. Arrastre un elemento **ExampleElement** desde el **cuadro de herramientas** a la superficie del diagrama.

5. En la ventana **propiedades** del elemento, seleccione la propiedad **espacio de nombres del elemento** y cambie el valor de **DefaultNamespace** a **OtherNamespace**.

     Observe que el valor del **espacio de nombres del elemento** ahora se muestra en negrita.

6. En la ventana **propiedades** , haga clic con el botón secundario en **espacio de nombres de elemento**y, a continuación, haga clic en **restablecer**.

     El valor de la propiedad se cambia a **DefaultNamespace**y el valor se muestra en una fuente normal.

     Vuelva a hacer clic con el botón secundario en **espacio de nombres del elemento** . El comando de **restablecimiento** ahora está deshabilitado porque la propiedad está actualmente en su estado de seguimiento.

7. Arrastre otro **ExampleElement** desde el **cuadro de herramientas** a la superficie del diagrama y cambie su **espacio de nombres de elemento** a **OtherNamespace**.

8. Haga clic en la superficie de diseño.

     En la ventana **propiedades** del diagrama, el valor de los **elementos personalizados** es ahora **1/2**.

9. Cambie el **espacio de nombres predeterminado** del diagrama de **DefaultNamespace** a **NewNamespace**.

     El **espacio de nombres** del primer elemento realiza un seguimiento de la propiedad del **espacio de nombres predeterminado** , mientras que el **espacio de nombres** del segundo elemento conserva su valor actualizado por el usuario de **OtherNamespace**.

10. Guarde la solución y, a continuación, cierre la compilación experimental.

## <a name="next-steps"></a>Pasos siguientes
 Si piensa usar más de una propiedad de seguimiento o implementar propiedades de seguimiento en más de un DSL, puede crear una plantilla de texto para generar el código común para admitir cada propiedad de seguimiento. Para obtener más información acerca de las plantillas de texto, vea [generación de código y plantillas de texto T4](../modeling/code-generation-and-t4-text-templates.md).

## <a name="see-also"></a>Vea también
 <xref:Microsoft.VisualStudio.Modeling.Design.TrackingPropertyDescriptor> <xref:Microsoft.VisualStudio.Modeling.Design.ElementTypeDescriptor>
 [Cómo definir un lenguaje específico de dominio](../modeling/how-to-define-a-domain-specific-language.md) [Cómo: crear una solución de lenguajes específicos de](../modeling/how-to-create-a-domain-specific-language-solution.md) dominio [Tutorial: personalizar la definición de lenguajes específicos de dominio](../misc/walkthrough-customizing-the-domain-specific-language-definition.md)
