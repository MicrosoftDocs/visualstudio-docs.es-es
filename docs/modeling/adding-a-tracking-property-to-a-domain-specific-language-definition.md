---
title: Adición de la propiedad de seguimiento a la definición de DSL
description: Obtenga información sobre la propiedad de dominio de seguimiento y cómo puede agregar una propiedad de seguimiento a un modelo de dominio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tracking properties [Domain-Specific Language Tools], walkthrough
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 546636ec3de4656bf0f6480dfaa5141d38e963d6
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384920"
---
# <a name="add-a-tracking-property-to-a-domain-specific-language-definition"></a>Agregar una propiedad de seguimiento a una definición de lenguaje específico de dominio

En este tutorial se muestra cómo agregar una propiedad de seguimiento a un modelo de dominio.

Una *propiedad de dominio de* seguimiento es una propiedad que el usuario puede actualizar, pero que tiene un valor predeterminado que se calcula mediante los valores de otras propiedades o elementos de dominio.

Por ejemplo, en Domain-Specific Language Tools (DSL Tools), la propiedad Nombre para mostrar de una clase de dominio tiene un valor predeterminado que se calcula mediante el nombre de la clase de dominio, pero un usuario puede cambiar el valor en tiempo de diseño o restablecerlo al valor calculado.

En este tutorial, creará un lenguaje específico de dominio (DSL) que tiene una propiedad de seguimiento de espacio de nombres que tiene un valor predeterminado basado en la propiedad Espacio de nombres predeterminado del modelo. Para obtener más información sobre las propiedades de seguimiento, vea [Definir propiedades de seguimiento.](/previous-versions/cc825929(v=vs.100))

- Las herramientas dsl admiten descriptores de propiedades de seguimiento. Sin embargo, el diseñador DSL no se puede usar para agregar una propiedad de seguimiento a un lenguaje. Por lo tanto, debe agregar código personalizado para definir e implementar la propiedad de seguimiento.

  Una propiedad de seguimiento tiene dos estados: seguimiento y actualizado por el usuario. Las propiedades de seguimiento tienen las siguientes características:

- Cuando se encuentra en estado de seguimiento, se calcula el valor de la propiedad de seguimiento y el valor se actualiza a medida que cambian otras propiedades del modelo.

- Cuando se actualiza por estado de usuario, el valor de la propiedad de seguimiento conserva el valor en el que el usuario estableció por última vez la propiedad.

- En la **ventana Propiedades,** el **comando Restablecer** de la propiedad de seguimiento solo está habilitado cuando la propiedad está en el estado actualizado por el usuario. El **comando Restablecer** establece el estado de la propiedad de seguimiento en seguimiento.

- En la **ventana** Propiedades, cuando la propiedad de seguimiento está en estado de seguimiento, su valor se muestra en una fuente normal.

- En la **ventana** Propiedades, cuando la propiedad de seguimiento está en el estado actualizado por el usuario, su valor se muestra en una fuente en negrita.

## <a name="prerequisites"></a>Requisitos previos

Para poder iniciar este tutorial, primero debe instalar estos componentes:

| Componente | Vínculo |
|-|-|
| Programa para la mejora | [http://go.microsoft.com/fwlink/?LinkID=185579](https://visualstudio.microsoft.com/) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkID=185580](/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts&preserve-view=true) |
| [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] | [http://go.microsoft.com/fwlink/?LinkID=185581](https://code.msdn.microsoft.com/site/search?query=%22Modeling%20SDK%22&f%5B0%5D.Value=%22Modeling%20SDK%22&f%5B0%5D.Type=SearchText&ac=5) |

## <a name="create-the-project"></a>Creación del proyecto

1. Cree un proyecto Domain-Specific Language Designer. Asígnale el nombre `TrackingPropertyDSL`.

2. En el **Asistente Diseñador de lenguaje específico de dominio ,** establezca las siguientes opciones:

    1. Seleccione la **plantilla MinimalLanguage.**

    2. Use el nombre predeterminado para el lenguaje específico del dominio, `TrackingPropertyDSL` .

    3. Establezca la extensión de los archivos de modelo en `trackingPropertyDsl` .

    4. Use el icono de plantilla predeterminado para los archivos de modelo.

    5. Establezca el nombre del producto en `Product Name` .

    6. Establezca el nombre de la empresa en `Company Name` .

    7. Use el valor predeterminado para el espacio de nombres raíz para los proyectos de la solución, `CompanyName.ProductName.TrackingPropertyDSL` .

    8. Permita que el asistente cree un archivo de clave de nombre fuerte para los ensamblados.

    9. Revise los detalles de la solución y, a continuación, haga clic **en Finalizar** para crear el proyecto de definición de DSL.

## <a name="customize-the-default-dsl-definition"></a>Personalización de la definición predeterminada de DSL
 En esta sección, personalizará la definición de DSL para que contenga los siguientes elementos:

- Propiedad de seguimiento de espacios de nombres para cada elemento del modelo.

- Propiedad IsNamespaceTracking booleana para cada elemento del modelo. Esta propiedad indicará si la propiedad de seguimiento está en estado de seguimiento o en el estado actualizado por el usuario.

- Propiedad De espacio de nombres predeterminado para el modelo. Esta propiedad se usará para calcular el valor predeterminado de la propiedad de seguimiento namespace.

- Propiedad calculada CustomElements para el modelo. Esta propiedad indicará la proporción de elementos que tienen un espacio de nombres personalizado.

### <a name="to-add-the-domain-properties"></a>Para agregar las propiedades de dominio

1. En el diseñador DSL, haga clic con el botón derecho en **la clase de dominio ExampleModel,** seleccione Agregar y, a continuación, haga clic en  **DomainProperty**.

    1. Asigne a la nueva propiedad el nombre `DefaultNamespace` .

    2. En la **ventana** Propiedades de la nueva propiedad, establezca **Valor predeterminado** en y `DefaultNamespace` Establezca **Tipo** en **Cadena.**

2. Para la **clase de dominio ExampleModel,** agregue una propiedad de dominio denominada `CustomElements` .

     En la **ventana** Propiedades de la nueva propiedad, establezca **Tipo** en **Calculado.**

3. Para la **clase de dominio ExampleElement,** agregue una propiedad de dominio denominada `Namespace` .

     En la **ventana** Propiedades de la nueva propiedad, establezca **Is Browsable** en **False** y **establezca Kind** en **CustomStorage.**

4. Para la **clase de dominio ExampleElement,** agregue una propiedad de dominio denominada `IsNamespaceTracking` .

     En la **ventana Propiedades** de la nueva propiedad, establezca **Is Browsable** en **False,** establezca **Valor** predeterminado en `true` y **Tipo** en **Boolean**.

### <a name="to-update-the-diagram-elements-and-dsl-details"></a>Para actualizar los elementos del diagrama y los detalles de DSL

1. En el diseñador DSL, haga clic con el botón derecho en la forma de geometría **ExampleShape,** seleccione **Agregar** y, a continuación, haga clic en **Decorador de texto.**

    1. Asigne al nuevo decorador de texto el nombre `NamespaceDecorator` .

    2. En la **ventana** Propiedades del decorador de texto, establezca **Posición** en **InnerBottomLeft.**

2. En el diseñador DSL, seleccione la línea que conecta la **clase ExampleElement** a la **forma ExampleShape.**

    1. En la **ventana Detalles de DSL,** seleccione la **pestaña Decorator Maps (Mapas de decorador).**

    2. En la **lista Decorators** , seleccione **NamespaceDecorator**, active su casilla y, a continuación, en la lista **Mostrar propiedades,** seleccione **Espacio de nombres**.

3. En **el Explorador DSL,** expanda la carpeta **Clases de** dominio, haga clic con el botón derecho en el nodo **ExampleElement** y, a continuación, haga clic **en Agregar nuevo descriptor de tipo de dominio**.

    1. Expanda el **nodo ExampleElement** y seleccione el nodo **Descriptor de tipo personalizado (Descriptor de tipo de** dominio).

    2. En la **ventana** Propiedades del descriptor de tipo de dominio, establezca **Custom Coded** en **True.**

4. En **el Explorador de DSL,** seleccione el nodo Comportamiento de **serialización** xml.

    1. En la **ventana** Propiedades, establezca **Carga posterior personalizada** en **True.**

## <a name="transform-templates"></a>Transformar plantillas

Ahora que ha definido las clases de dominio y las propiedades del DSL, puede comprobar que la definición de DSL se puede transformar correctamente para volver a generar el código del proyecto.

1. En la barra **Explorador de soluciones** de herramientas, haga clic **en Transformar todas las plantillas.**

2. El sistema vuelve a generar el código de la solución y guarda DslDefinition.dsl. Para obtener información sobre el formato XML de los archivos de definición, vea [El archivo DslDefinition.dsl](../modeling/the-dsldefinition-dsl-file.md).

## <a name="create-files-for-custom-code"></a>Crear archivos para código personalizado

Al transformar todas las plantillas, el sistema genera el código fuente que define el lenguaje específico del dominio en los proyectos Dsl y DslPackage. Para evitar interferir con el texto generado, escriba el código personalizado en archivos distintos de los archivos de código generados.

Debe proporcionar código para mantener el valor y el estado de la propiedad de seguimiento. Para ayudarle a distinguir el código personalizado del código generado y evitar conflictos de nomenclatura de archivos, coloque los archivos de código personalizados en una subcarpeta independiente.

1. En **Explorador de soluciones**, haga clic con el botón derecho en el **proyecto DSL,** seleccione **Agregar** y, a continuación, haga clic en **Nueva carpeta**. Asigne a la nueva carpeta el nombre `CustomCode` .

2. Haga clic con el botón derecho **en la nueva carpeta CustomCode,** seleccione **Agregar** y, a continuación, haga clic en **Nuevo elemento**.

3. Seleccione la **plantilla Archivo de** código, establezca el **nombre** en `NamespaceTrackingProperty.cs` y, a continuación, haga clic **en Aceptar.**

     El archivo NamespaceTrackingProperty.cs se crea y se abre para su edición.

4. En la carpeta , cree los siguientes archivos de código: `ExampleModel.cs,``HelperClasses.cs` `Serialization.cs` , y `TypeDescriptor.cs` .

5. En el **proyecto DslPackage,** cree también una `CustomCode` carpeta y agrégréle un archivo `Package.cs` de código.

## <a name="add-helper-classes-to-support-tracking-properties"></a>Agregar clases auxiliares para admitir propiedades de seguimiento

Para el archivo HelperClasses.cs, agregue las `TrackingHelper` clases y como se muestra a `CriticalException` continuación. Hará referencia a estas clases más adelante en este tutorial.

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

## <a name="add-custom-code-for-the-custom-type-descriptor"></a>Agregar código personalizado para el descriptor de tipo personalizado

Implemente `GetCustomProperties` el método para el descriptor de tipos para la clase de `ExampleModel` dominio.

> [!NOTE]
> Código que las herramientas DSL generan para el descriptor de tipos personalizado para las llamadas ; sin embargo, las herramientas dsl no generan código `ExampleModel` `GetCustomProperties` que implemente el método .

Al definir este método, se crea el descriptor de propiedad de seguimiento para la propiedad de seguimiento Namespace. Además, proporcionar atributos para la propiedad de seguimiento permite que la **ventana** Propiedades muestre la propiedad correctamente.

### <a name="to-modify-the-type-descriptor-for-the-examplemodel-domain-class"></a>Para modificar el descriptor de tipo para la clase de dominio ExampleModel

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

El código generado define un proveedor de descripción de tipos para la clase de dominio ExampleElement; sin embargo, debe agregar código para indicar al DSL que use este proveedor de descripción de tipos.

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

## <a name="add-custom-code-for-the-model"></a>Agregar código personalizado para el modelo

Implemente `GetCustomElementsValue` el método para la clase de `ExampleModel` dominio.

> [!NOTE]
> Código que las herramientas DSL generan para las llamadas ; sin embargo, las herramientas dsl no `ExampleModel` `GetCustomElementsValue` generan código que implemente el método .

La `GetCustomElementsValue` definición del método proporciona la lógica para la propiedad calculada CustomElements de `ExampleModel` . Este método cuenta el número de clases de dominio que tienen una propiedad de seguimiento namespace que tiene un valor actualizado por el usuario y devuelve una cadena que representa este recuento como proporción de los elementos totales del `ExampleElement` modelo.

Además, agregue un método a `OnDefaultNamespaceChanged` `ExampleModel` e invalide el método de la `OnValueChanged` clase anidada de para llamar a `DefaultNamespacePropertyHandler` `ExampleModel` `OnDefaultNamespaceChanged` .

Dado que la propiedad DefaultNamespace se usa para calcular la propiedad de seguimiento namespace, debe notificar a todas las clases de dominio que el valor `ExampleModel` `ExampleElement` de DefaultNamespace ha cambiado.

### <a name="to-modify-the-property-handler-for-the-tracked-property"></a>Para modificar el controlador de propiedades de la propiedad de la que se realiza el seguimiento

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

## <a name="add-custom-code-for-the-tracking-property"></a>Agregar código personalizado para la propiedad Tracking

Agregue un `CalculateNamespace` método a la clase de `ExampleElement` dominio.

La definición de este método proporciona la lógica para la propiedad calculada CustomElements de `ExampleModel` . Este método cuenta el número de clases de dominio que tienen una propiedad de seguimiento namespace que se encuentra en el estado actualizado por el usuario y devuelve una cadena que representa este recuento como una proporción de los elementos totales del `ExampleElement` modelo.

Además, agregue almacenamiento para los métodos y para obtener y establecer la propiedad de almacenamiento personalizado Namespace de la `ExampleElement` clase de dominio.

> [!NOTE]
> El código que generan las herramientas DSL para llama a los métodos get y set; sin embargo, las herramientas dsl no generan código `ExampleModel` que implemente los métodos.

### <a name="to-add-the-method-for-the-custom-type-descriptor"></a>Para agregar el método para el descriptor de tipo personalizado

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

## <a name="add-custom-code-to-support-serialization"></a>Agregar código personalizado para admitir la serialización

Agregue código para admitir el comportamiento de carga posterior personalizado para la serialización XML.

> [!NOTE]
> El código que generan las herramientas DSL llama a los métodos y ; sin embargo, las herramientas dsl no generan código `OnPostLoadModel` `OnPostLoadModelAndDiagram` que implemente estos métodos.

### <a name="to-add-code-to-support-the-custom-post-load-behavior"></a>Para agregar código para admitir el comportamiento personalizado posterior a la carga

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

## <a name="test-the-language"></a>Probar el idioma

El siguiente paso consiste en compilar y ejecutar el diseñador DSL en una nueva instancia de para que pueda comprobar que la propiedad de seguimiento [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] funciona correctamente.

1. En el menú **Compilar**, haga clic en **Recompilar solución**.

2. En el menú **Depurar**, haga clic en **Iniciar depuración**.

    La compilación experimental de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] abre **la solución Depuración,** que contiene un archivo de prueba vacío.

3. En **Explorador de soluciones**, haga doble clic en el archivo Test.trackingPropertyDsl para abrirlo en el diseñador y, a continuación, haga clic en la superficie de diseño.

    Observe que en la **ventana** Propiedades  del diagrama, la propiedad Espacio de nombres predeterminado es **DefaultNamespace** y la propiedad **Elementos** personalizados **es 0/0.**

4. Arrastre un **elemento ExampleElement** desde el cuadro **de herramientas** a la superficie del diagrama.

5. En la **ventana Propiedades** del elemento , seleccione la propiedad Espacio de nombres **de** elemento y cambie el valor de **DefaultNamespace** a **OtherNamespace.**

    Observe que el valor de **Espacio de nombres de** elemento ahora se muestra en negrita.

6. En la ventana **Propiedades,** haga clic con el botón derecho en **Espacio de nombres de** elemento y, a continuación, haga clic en **Restablecer**.

    El valor de la propiedad se cambia a **DefaultNamespace** y el valor se muestra en una fuente normal.

    Vuelva a hacer clic con el **botón derecho en Espacio de nombres de** elemento. El **comando Restablecer** ahora está deshabilitado porque la propiedad está actualmente en su estado de seguimiento.

7. Arrastre otro **ExampleElement desde** el Cuadro **de herramientas** a la superficie del diagrama y cambie su espacio de nombres **de** elemento a **OtherNamespace.**

8. Haga clic en la superficie de diseño.

    En la **ventana** Propiedades del diagrama, el valor de **Elementos** personalizados ahora es **1/2**.

9. Cambie **el espacio de** nombres predeterminado del diagrama de **DefaultNamespace** a **NewNamespace.**

     El **espacio de** nombres del primer elemento realiza  un seguimiento de la propiedad **Espacio** de nombres predeterminado, mientras que el espacio de nombres del segundo elemento conserva su valor actualizado por el usuario **de OtherNamespace**.

10. Guarde la solución y cierre la compilación experimental.

## <a name="next-steps"></a>Pasos siguientes

Si planea usar más de una propiedad de seguimiento o implementar propiedades de seguimiento en más de un DSL, puede crear una plantilla de texto para generar el código común para admitir cada propiedad de seguimiento. Para obtener más información sobre las plantillas de texto, vea [Generación de código y Plantillas de texto T4](../modeling/code-generation-and-t4-text-templates.md).

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.Modeling.Design.TrackingPropertyDescriptor>
- <xref:Microsoft.VisualStudio.Modeling.Design.ElementTypeDescriptor>
- [Cómo definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md)
- [Cómo: Crear soluciones de lenguajes específicos de dominio](../modeling/how-to-create-a-domain-specific-language-solution.md)