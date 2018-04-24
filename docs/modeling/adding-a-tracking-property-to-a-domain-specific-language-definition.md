---
title: Agregar una propiedad de seguimiento a una definición de lenguaje específico de dominio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tracking properties [Domain-Specific Language Tools], walkthrough
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: c7adc5408ff1269196e5093fb3ff0a1c6d4e2ef8
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="add-a-tracking-property-to-a-domain-specific-language-definition"></a>Agregar una propiedad de seguimiento a una definición de lenguaje específico de dominio

Este tutorial muestra cómo agregar una propiedad de seguimiento a un modelo de dominio.

A *seguimiento dominio* es una propiedad que se pueden actualizar por el usuario, pero que tiene un valor predeterminado que se calcula utilizando los valores de otras propiedades del dominio o los elementos.

Por ejemplo, en las herramientas de lenguaje específico de dominio (herramientas ADSL), el nombre para mostrar propiedades de una clase de dominio tiene un valor predeterminado que se calcula utilizando el nombre de la clase de dominio, pero un usuario puede cambiar el valor en tiempo de diseño o restablecer el valor calculado.

En este tutorial, creará un lenguaje específico de dominio (DSL) que tiene una propiedad que tiene un valor predeterminado basado en la propiedad Namespace predeterminado del modelo de seguimiento de Namespace. Para obtener más información sobre el seguimiento de propiedades, vea [definir propiedades de seguimiento](http://msdn.microsoft.com/0538b0e4-6221-4e7d-911a-b92cd622f0be).

-   La compatibilidad de herramientas DSL descriptores de propiedades de seguimiento. Sin embargo, el diseñador DSL no puede utilizarse para agregar una propiedad de seguimiento en un idioma. Por lo tanto, debe agregar código personalizado para definir e implementar la propiedad de seguimiento.

 Una propiedad de seguimiento tiene dos estados: hacer un seguimiento y actualizados por el usuario. Propiedades de seguimiento tienen las siguientes características:

-   Cuando se encuentra en el estado de seguimiento, se calcula el valor de la propiedad de seguimiento y el valor se actualiza como otras propiedades en el cambio de modelo.

-   Cuando en la sección actualizada por estado de usuario, el valor de la propiedad de seguimiento conserva el valor en el que el usuario última establece la propiedad.

-   En el **propiedades** ventana, el **restablecer** comando para la propiedad de seguimiento solo se habilita cuando la propiedad está en la sección actualizada por estado de usuario. El **restablecer** comando establece la propiedad de seguimiento de estado de seguimiento.

-   En el **propiedades** ventana, cuando la propiedad de seguimiento está en el estado de seguimiento, su valor se muestra en un formato de fuente normal.

-   En el **propiedades** ventana, cuando la propiedad de seguimiento está en la sección actualizada por estado de usuario, su valor se muestra en negrita.

## <a name="prerequisites"></a>Requisitos previos

Antes de empezar este tutorial, primero debe instalar estos componentes:

|||
|-|-|
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185579](http://go.microsoft.com/fwlink/?LinkID=185579)|
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185580](http://go.microsoft.com/fwlink/?LinkID=185580)|
|[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185581](http://go.microsoft.com/fwlink/?LinkID=185581)|

## <a name="create-the-project"></a>Crear el proyecto

1.  Cree un proyecto de diseñador de lenguaje específico de dominio. Denomínelo `TrackingPropertyDSL`.

2.  En el **Asistente del Diseñador de lenguaje específico de dominio**, establezca las siguientes opciones:

    1.  Seleccione el **MinimalLanguage** plantilla.

    2.  Use el nombre predeterminado para el lenguaje específico de dominio, `TrackingPropertyDSL`.

    3.  Establecer la extensión para los archivos de modelo para `trackingPropertyDsl`.

    4.  Utilice el icono de plantilla predeterminada para los archivos de modelo.

    5.  Establecer el nombre del producto se `Product Name`.

    6.  Establecer el nombre de la compañía a `Company Name`.

    7.  Usar el valor predeterminado para el espacio de nombres raíz para los proyectos de la solución `CompanyName.ProductName.TrackingPropertyDSL`.

    8.  Permitir que el Asistente para crear un archivo de clave de nombre seguro para los ensamblados.

    9. Revise los detalles de la solución y, a continuación, haga clic en **finalizar** para crear el proyecto de definición DSL.

## <a name="customize-the-default-dsl-definition"></a>Personalizar la definición de DSL predeterminada
 En esta sección, personalizar la definición DSL para contener los elementos siguientes:

-   Una propiedad para cada elemento del modelo de seguimiento de Namespace.

-   Una propiedad booleana IsNamespaceTracking para cada elemento del modelo. Esta propiedad indicará si la propiedad de seguimiento está en el estado de seguimiento o en la sección actualizada por estado de usuario.

-   Una propiedad Namespace predeterminado para el modelo. Esta propiedad se utilizará para calcular el valor predeterminado de la propiedad de seguimiento de Namespace.

-   Una propiedad CustomElements calculados para el modelo. Esta propiedad indicará la proporción de elementos que tienen un espacio de nombres personalizado.

### <a name="to-add-the-domain-properties"></a>Para agregar las propiedades del dominio

1.  En el diseñador DSL, haga clic en el **ExampleModel** clase de dominio, seleccione **agregar**y, a continuación, haga clic en **y**.

    1.  Nombre de la nueva propiedad `DefaultNamespace`.

    2.  En el **propiedades** ventana para la nueva propiedad, establezca **Default Value** a `DefaultNamespace`y establezca **tipo** a **cadena**.

2.  Para el **ExampleModel** dominio clase, agregue una propiedad de dominio denominada `CustomElements`.

     En el **propiedades** ventana para la nueva propiedad, establezca **tipo** a **calculado**.

3.  Para el **ExampleElement** dominio clase, agregue una propiedad de dominio denominada `Namespace`.

     En el **propiedades** ventana para la nueva propiedad, establezca **es examinable** a **False**y establezca **tipo** a **CustomStorage** .

4.  Para el **ExampleElement** dominio clase, agregue una propiedad de dominio denominada `IsNamespaceTracking`.

     En el **propiedades** ventana para la nueva propiedad, establezca **es examinable** a **False**, establezca **Default Value** a `true`y establezca **Tipo** a **booleano**.

### <a name="to-update-the-diagram-elements-and-dsl-details"></a>Para actualizar los elementos del diagrama y los detalles de DSL

1.  En el diseñador DSL, haga clic en el **ExampleShape** forma geométrica, seleccione **agregar**y, a continuación, haga clic en **texto decorador**.

    1.  El nombre de la nueva decorador texto `NamespaceDecorator`.

    2.  En el **propiedades** ventana para el elemento decorator de texto, establezca **posición** a **InnerBottomLeft**.

2.  En el diseñador DSL, seleccione la línea que conecta el **ExampleElement** clase a la **ExampleShape** forma.

    1.  En el **detalles de DSL** ventana, seleccione la **decorador mapas** ficha.

    2.  En el **decoradores** lista, seleccione **NamespaceDecorator**, active la casilla correspondiente y, a continuación, en la **Mostrar propiedad** lista, seleccione **Namespace**.

3.  En **DSL explorador**, expanda la **clases de dominio** carpeta, haga clic en el **ExampleElement** nodo y, a continuación, haga clic en **Agregar nuevo dominio Descriptor de tipo**.

    1.  Expanda el **ExampleElement** y seleccione el **Descriptor de tipos personalizado (Descriptor de tipo de dominio)** nodo.

    2.  En el **propiedades** ventana para el descriptor de tipo de dominio, establezca **personalizado codificadas** a **True**.

4.  En **DSL explorador**, seleccione la **un comportamiento de serialización Xml** nodo.

    1.  En el **propiedades** ventana, establezca **personalizado Post carga** a **True**.

## <a name="transform-templates"></a>Transformar plantillas

Ahora que ha definido las propiedades y clases de dominio para ADSL, puede comprobar que se puede transformar correctamente la definición DSL para volver a generar el código para el proyecto.

1.  En el **el Explorador de soluciones** barra de herramientas, haga clic en **Transformar todas las plantillas**.

2.  El sistema vuelve a generar el código de la solución y guarda DslDefinition.dsl. Para obtener información sobre el formato XML de archivos de definición, consulte [el archivo DslDefinition.dsl](../modeling/the-dsldefinition-dsl-file.md).

## <a name="create-files-for-custom-code"></a>Crear archivos de código personalizado

Al transformar todas las plantillas, el sistema genera el código fuente que define el lenguaje específico de dominio en los proyectos de Dsl y DslPackage. Por lo que puede evitar la interferencia con el texto generado, escribir el código personalizado en los archivos que son distintos de los archivos de código generado.

Debe proporcionar código para mantener el valor y el estado de la propiedad de seguimiento. Para ayudar a distinguir el código personalizado en el código generado y para evitar conflictos de nomenclatura de archivos, coloque los archivos de código personalizado en una carpeta distinta.

1.  En **el Explorador de soluciones**, haga clic en el **DSL** , seleccione **agregar**y, a continuación, haga clic en **nueva carpeta**. Nombre de la nueva carpeta `CustomCode`.

2.  Haga clic en el nuevo **CustomCode** carpeta, seleccione **agregar**y, a continuación, haga clic en **nuevo elemento**.

3.  Seleccione el **archivo de código** plantilla, establezca la **nombre** a `NamespaceTrackingProperty.cs`y, a continuación, haga clic en **Aceptar**.

     El archivo NamespaceTrackingProperty.cs se creó y se abre para su edición.

4.  En la carpeta, cree los siguientes archivos de código: `ExampleModel.cs,``HelperClasses.cs`, `Serialization.cs`, y `TypeDescriptor.cs`.

5.  En el **DslPackage** proyecto de equipo y también crear un `CustomCode` carpeta y agregarle un `Package.cs` archivo de código.

## <a name="add-helper-classes-to-support-tracking-properties"></a>Agregar clases auxiliares para admitir el seguimiento de propiedades

En el archivo HelperClasses.cs, agregue el `TrackingHelper` y `CriticalException` clases como se indica a continuación. Se hará referencia a estas clases más adelante en este tutorial.

1.  Agregue el código siguiente al archivo HelperClasses.cs.

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

## <a name="add-custom-code-for-the-custom-type-descriptor"></a>Agregar código personalizado para el Descriptor de tipos personalizado

Implemente el `GetCustomProperties` método para el descriptor de tipo para el `ExampleModel` clase de dominio.

> [!NOTE]
> El código que generan las herramientas DSL para el descriptor de tipos personalizado para `ExampleModel` llamadas `GetCustomProperties`; sin embargo, las herramientas DSL no generan código que implementa el método.

La definición de este método crea el seguimiento de descriptor de propiedad para la propiedad de seguimiento de Namespace. Además, proporciona los atributos para la propiedad de seguimiento permite la **propiedades** ventana para mostrar la propiedad correctamente.

### <a name="to-modify-the-type-descriptor-for-the-examplemodel-domain-class"></a>Para modificar el descriptor de tipo para la clase de dominio ExampleModel

1.  Agregue el código siguiente al archivo TypeDescriptor.cs.

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

El código generado define un proveedor de descripción de tipos para la clase de dominio ExampleElement; Sin embargo, debe agregar código para indicar la DSL para usar este proveedor de descripción de tipo.

1.  Agregue el código siguiente al archivo Package.cs.

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

## <a name="add-custom-code-for-the-model"></a>Agregar código personalizado para el modelo

Implemente el `GetCustomElementsValue` método para el `ExampleModel` clase de dominio.

> [!NOTE]
> El código que generan las herramientas DSL para `ExampleModel` llamadas `GetCustomElementsValue`; sin embargo, las herramientas DSL no generan código que implementa el método.

Definir la `GetCustomElementsValue` método proporciona la lógica para la propiedad CustomElements calculado de `ExampleModel`. Este método cuenta el número de `ExampleElement` las clases de dominio que tienen una propiedad que tiene un valor actualizado por el usuario y devuelve una cadena que representa este número como una proporción del total los elementos del modelo de seguimiento de Namespace.

Además, agregar un `OnDefaultNamespaceChanged` método `ExampleModel`e invalidar el `OnValueChanged` método de la `DefaultNamespacePropertyHandler` anidada de la clase de `ExampleModel` para llamar a `OnDefaultNamespaceChanged`.

Dado que la propiedad DefaultNamespace se usa para calcular el Namespace tracking (propiedad), `ExampleModel` debe notificar todos `ExampleElement` clases de dominio que ha cambiado el valor de DefaultNamespace.

### <a name="to-modify-the-property-handler-for-the-tracked-property"></a>Para modificar el controlador de propiedad para la propiedad sometidas a seguimiento

1.  Agregue el código siguiente al archivo ExampleModel.cs.

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

## <a name="add-custom-code-for-the-tracking-property"></a>Agregar código personalizado para la propiedad de seguimiento

Agregar un `CalculateNamespace` método a la `ExampleElement` clase de dominio.

Definición de este método proporciona la lógica para la propiedad CustomElements calculado de `ExampleModel`. Este método cuenta el número de `ExampleElement` las clases de dominio que tienen una propiedad que se encuentra en los archivos de seguimiento de Namespace por estado de usuario y devuelve una cadena que representa este número como una proporción del total los elementos del modelo.

También, agregar almacenamiento para y métodos para obtener y establecer la propiedad de almacenamiento personalizados Namespace de la `ExampleElement` clase de dominio.

> [!NOTE]
> El código que generan las herramientas DSL para `ExampleModel` llama a get y establecer métodos; sin embargo, las herramientas DSL no generan código que implementa los métodos.

### <a name="to-add-the-method-for-the-custom-type-descriptor"></a>Para agregar el método de descriptor de tipos personalizado

1.  Agregue el código siguiente al archivo NamespaceTrackingProperty.cs.

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

## <a name="add-custom-code-to-support-serialization"></a>Agregar código personalizado para admitir la serialización

Agregue código para admitir el comportamiento personalizado de posterior a la carga para la serialización XML.

> [!NOTE]
> El código que las herramientas DSL generar llamadas el `OnPostLoadModel` y `OnPostLoadModelAndDiagram` métodos; sin embargo, las herramientas DSL no generan código que implementa estos métodos.

### <a name="to-add-code-to-support-the-custom-post-load-behavior"></a>Para agregar código para admitir el comportamiento de posterior a la carga personalizado

1.  Agregue el código siguiente al archivo Serialization.cs.

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

## <a name="test-the-language"></a>El lenguaje de prueba

El paso siguiente consiste en compilar y ejecutar el diseñador DSL en una nueva instancia de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] para que pueda comprobar que la propiedad de seguimiento funciona correctamente.

1.  En el **generar** menú, haga clic en **volver a generar solución**.

2.  En el menú **Depurar**, haga clic en **Iniciar depuración**.

     La compilación experimental de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] abre el **depuración** solución, que contiene un archivo de prueba vacía.

3.  En **el Explorador de soluciones**, haga doble clic en el archivo Test.trackingPropertyDsl para abrirlo en el diseñador y, a continuación, haga clic en la superficie de diseño.

     Tenga en cuenta que en el **propiedades** ventana para el diagrama, el **Default Namespace** propiedad es **DefaultNamespace**y el **personalizado elementos** propiedad es **0/0**.

4.  Arrastre un **ExampleElement** elemento desde el **cuadro de herramientas** a la superficie del diagrama.

5.  En el **propiedades** ventana para el elemento, seleccione la **elemento Namespace** propiedad y cambie el valor de **DefaultNamespace** a  **OtherNamespace**.

     Tenga en cuenta que el valor de **elemento Namespace** ahora se muestra en negrita.

6.  En el **propiedades** ventana, haga clic en **elemento Namespace**y, a continuación, haga clic en **restablecer**.

     El valor de la propiedad se cambia a **DefaultNamespace**, y se muestra el valor en un formato de fuente normal.

     Haga clic en **elemento Namespace** nuevo. El **restablecer** comando ahora está deshabilitado debido a la propiedad está en su estado de seguimiento.

7.  Arrastre otra **ExampleElement** desde el **cuadro de herramientas** a la superficie del diagrama y cambie su **elemento Namespace** a **OtherNamespace**.

8.  Haga clic en la superficie de diseño.

     En el **propiedades** ventana para el diagrama, el valor de **personalizado elementos** es ahora **1/2**.

9. Cambio **Default Namespace** para el diagrama de **DefaultNamespace** a **NewNamespace**.

     El **Namespace** de seguimiento que el primer elemento del **Default Namespace** propiedad, mientras que la **Namespace** del segundo elemento mantiene su valor actualizado de usuario de  **OtherNamespace**.

10. Guarde la solución y, a continuación, cierre la compilación experimental.

## <a name="next-steps"></a>Pasos siguientes

Si tiene previsto utilizar seguimiento de más de una propiedad o implementar propiedades de seguimiento en más de un DSL, puede crear una plantilla de texto para generar el código común para admitir cada propiedad de seguimiento. Para obtener más información acerca de las plantillas de texto, consulte [generación de código y plantillas de texto T4](../modeling/code-generation-and-t4-text-templates.md).

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.Modeling.Design.TrackingPropertyDescriptor>
- <xref:Microsoft.VisualStudio.Modeling.Design.ElementTypeDescriptor>
- [Cómo definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md)
- [Cómo: Crear soluciones de lenguajes específicos de dominio](../modeling/how-to-create-a-domain-specific-language-solution.md)
