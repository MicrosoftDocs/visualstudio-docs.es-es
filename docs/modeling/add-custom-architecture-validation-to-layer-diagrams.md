---
title: Agregar validación de arquitectura personalizada a diagramas de dependencia
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, adding custom validation
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 34898bff2b437c84a29cec31091205044367abec
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652324"
---
# <a name="add-custom-architecture-validation-to-dependency-diagrams"></a>Agregar validación de arquitectura personalizada a diagramas de dependencia

En Visual Studio, los usuarios pueden validar el código fuente de un proyecto con un modelo de capas para que puedan comprobar que el código fuente cumple las dependencias de un diagrama de dependencia. Hay un algoritmo de validación estándar, pero puede definir sus propias extensiones de validación.

Cuando el usuario selecciona el comando **validar arquitectura** en un diagrama de dependencia, se invoca el método de validación estándar, seguido de cualquier extensión de validación que se haya instalado.

> [!NOTE]
> En un diagrama de dependencia, el propósito principal de la validación es comparar el diagrama con el código de programa de otras partes de la solución.

Puede empaquetar la extensión de validación de capas en una extensión de integración de Visual Studio (VSIX), que puede distribuir a otros usuarios de Visual Studio. Puede colocar el validador en VSIX por sí solo o puede combinarlo en el mismo VSIX con otras extensiones. Debe escribir el código del validador en su propio proyecto de Visual Studio, no en el mismo proyecto que otras extensiones.

> [!WARNING]
> Después de haber creado un proyecto de validación, copie el [código de ejemplo](#example) que aparece al final de este tema y después, edítelo, en función de sus necesidades.

## <a name="requirements"></a>Requisitos

Vea [Requisitos](../modeling/extend-layer-diagrams.md#requirements).

## <a name="defining-a-layer-validator-in-a-new-vsix"></a>Definir un validador de capas en un nuevo VSIX

El método más rápido para crear un validador consiste en usar la plantilla de proyecto. Esto coloca el código y el manifiesto de VSIX en el mismo proyecto.

### <a name="to-define-an-extension-by-using-a-project-template"></a>Para definir una extensión mediante una plantilla de proyecto

1. Cree un nuevo proyecto de **extensión de validación del diseñador de capas** .

    La plantilla crea un proyecto que contiene un pequeño ejemplo.

   > [!WARNING]
   > Para que la plantilla funcione correctamente:
   >
   > - Edite las llamadas a `LogValidationError` para quitar los argumentos opcionales `errorSourceNodes` y `errorTargetNodes`.
   > - Si usa propiedades personalizadas, aplique la actualización mencionada en [Agregar propiedades personalizadas a diagramas de dependencia](../modeling/add-custom-properties-to-layer-diagrams.md).

2. Modifique el código para definir la validación. Para obtener más información, vea [Programar la validación](#programming).

3. Para probar la extensión, vea [Depurar la validación de capas](#debugging).

   > [!NOTE]
   > Solo se llamará al método en circunstancias concretas y los puntos de interrupción no funcionarán automáticamente. Para obtener más información, vea [Depurar la validación de capas](#debugging).

::: moniker range="vs-2017"

4. Para instalar la extensión en la instancia principal de Visual Studio o en otro equipo, busque el archivo *. vsix* en el directorio *bin* . Cópielo en el equipo donde desea instalarlo y, a continuación, haga doble clic en él. Para desinstalarlo, elija **extensiones y actualizaciones** en el menú **herramientas** .

::: moniker-end

::: moniker range=">=vs-2019"

4. Para instalar la extensión en la instancia principal de Visual Studio o en otro equipo, busque el archivo *. vsix* en el directorio *bin* . Cópielo en el equipo donde desea instalarlo y, a continuación, haga doble clic en él. Para desinstalarlo, elija **administrar extensiones** en el menú **extensiones** .

::: moniker-end

## <a name="adding-a-layer-validator-to-a-separate-vsix"></a>Agregar un validador de capas a un VSIX independiente

Si desea crear un VSIX que contenga validadores de capas, comandos y otras extensiones, le recomendamos que cree un proyecto para definir VSIX y proyectos independientes para los controladores.

### <a name="to-add-layer-validation-to-a-separate-vsix"></a>Para agregar la validación de capas a un VSIX independiente

1. Cree un proyecto de **Biblioteca de clases**. Este proyecto contendrá la clase de validación de capas.

2. Busque o cree un **Proyecto VSIX** en la solución. Un proyecto de VSIX contiene un archivo denominado **source.extension.vsixmanifest**.

3. En **Explorador de soluciones**, en el menú contextual del Proyecto VSIX, elija **establecer como proyecto de inicio**.

4. En **source.extension.vsixmanifest**, en **Activos**, agregue el proyecto de validación de capas como componente MEF:

    1. Elija **Nuevo**.

    2. En el cuadro de diálogo **Agregar nuevo activo** , establezca:

         **Tipo** = **Microsoft.VisualStudio.MefComponent**

         **Origen** = **Un proyecto de la solución actual**

         **Proyecto** = *El proyecto validador*

5. También debe agregarse como validación de capas:

    1. Elija **Nuevo**.

    2. En el cuadro de diálogo **Agregar nuevo activo** , establezca:

         **Tipo** = **Microsoft.VisualStudio.ArchitectureTools.Layer.Validator**. Esta no es una de las opciones de la lista desplegable. Debe escribirla desde el teclado.

         **Origen** = **Un proyecto de la solución actual**

         **Proyecto** = *El proyecto validador*

6. Vuelva al proyecto de validación de capas y agregue las siguientes referencias de proyecto:

    |**Referencia**|**Qué permite hacer**|
    |-|-|
    |Microsoft.VisualStudio.GraphModel.dll|Leer el gráfico de la arquitectura|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema.dll|Leer el código que DOM asoció a las capas|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|Leer el modelo de capas|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility|Leer y actualizar formas y diagramas.|
    |System.ComponentModel.Composition|Definir el componente de validación mediante MEF (Managed Extensibility Framework)|
    |Microsoft.VisualStudio.Modeling.Sdk.[versión]|Definir las extensiones de modelado|

7. Copie el código de ejemplo al final de este tema en el archivo de clase del proyecto de biblioteca de validador para que contenga el código de la validación. Para obtener más información, vea [Programar la validación](#programming).

8. Para probar la extensión, vea [Depurar la validación de capas](#debugging).

    > [!NOTE]
    > Solo se llamará al método en circunstancias concretas y los puntos de interrupción no funcionarán automáticamente. Para obtener más información, vea [Depurar la validación de capas](#debugging).

9. Para instalar VSIX en la instancia principal de Visual Studio, o en otro equipo, busque el archivo **. vsix** en el directorio **bin** del Proyecto VSIX. Cópielo en el equipo donde desea instalar VSIX. En el Explorador de Windows, haga doble clic en el archivo VSIX.

## <a name="programming"></a> Programar la validación

Para definir una extensión de validación de capas, defina una clase que tenga las siguientes características:

- El formato general de la declaración será similar al siguiente:

  ```csharp
  using System.ComponentModel.Composition;
  using Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema;
  using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
  using Microsoft.VisualStudio.GraphModel;
  ...
   [Export(typeof(IValidateArchitectureExtension))]
    public partial class Validator1Extension :
                    IValidateArchitectureExtension
    {
      public void ValidateArchitecture(Graph graph)
      {
         GraphSchema schema = graph.DocumentSchema;
        ...
    } }
  ```

- Al detectar un error, puede notificarlo mediante `LogValidationError()`.

  > [!WARNING]
  > No use los parámetros opcionales de `LogValidationError`.

Cuando el usuario invoca el comando de menú **Validar arquitectura** , el sistema en tiempo de ejecución de capas analiza las capas y sus artefactos para generar un gráfico. El gráfico tiene cuatro partes:

- Modelos de capas de la solución de Visual Studio que se representan como nodos y vínculos en el gráfico.

- El código, los elementos de proyecto y otros artefactos definidos en la solución y representados como nodos, y los vínculos que representan las dependencias detectadas por el proceso de análisis.

- Los vínculos de los nodos de capa a los nodos de artefacto de código.

- Los nodos que representan los errores detectados por el validador.

Cuando se ha construido el gráfico, se llama al método de validación estándar. Una vez completado, se llama en un orden no especificado a los métodos de validación de extensiones instalados. El gráfico se pasa a cada método de `ValidateArchitecture` , que puede examinar el gráfico y notificar los errores que encuentre.

> [!NOTE]
> Esto no es lo mismo que el proceso de validación que se puede usar en lenguajes específicos de dominio.

Los métodos de validación no deben cambiar el modelo de capas ni el código que se valida.

El modelo del gráfico se define en <xref:Microsoft.VisualStudio.GraphModel>. Sus clases principales son <xref:Microsoft.VisualStudio.GraphModel.GraphNode> y <xref:Microsoft.VisualStudio.GraphModel.GraphLink>.

Cada nodo y cada vínculo tiene una o más categorías que especifican el tipo de elemento o relación que representa. Los nodos de un gráfico típico tienen las siguientes categorías:

- Dsl.LayerModel

- Dsl.Layer

- Dsl.Reference

- CodeSchema_Type

- CodeSchema_Namespace

- CodeSchema_Type

- CodeSchema_Method

- CodeSchema_Field

- CodeSchema_Property

Los vínculos entre las capas y los elementos del código tienen la categoría "Representa".

## <a name="debugging"></a> Depurar la validación

Para depurar la extensión de validación de capas, presione CTRL+F5. Se abre una instancia experimental de Visual Studio. En esta instancia, abra o cree un modelo de capas. Este modelo debe estar asociado a código y debe tener al menos una dependencia.

### <a name="test-with-a-solution-that-contains-dependencies"></a>Probar con una solución que contiene dependencias

No se ejecuta la validación a menos que estén presentes las siguientes características:

- Hay al menos un vínculo de dependencia en el diagrama de dependencia.

- Hay capas del modelo asociadas a elementos de código.

La primera vez que inicia una instancia experimental de Visual Studio para probar la extensión de validación, abra o cree una solución que tenga estas características.

### <a name="run-clean-solution-before-validate-architecture"></a>Ejecutar Limpiar solución antes de validar la arquitectura

Cada vez que actualice el código de validación, use el comando **Limpiar solución** en el menú **Compilar** de la solución experimental antes de probar el comando Validar. Esto es necesario porque los resultados de la validación se almacenan en memoria caché. Si no ha actualizado el diagrama de dependencias de prueba o su código, no se ejecutarán los métodos de validación.

### <a name="launch-the-debugger-explicitly"></a>Iniciar el depurador explícitamente

La validación se ejecuta en un proceso independiente. Por consiguiente, los puntos de interrupción del método de validación no se activarán. Debe adjuntar explícitamente el depurador al proceso cuando se haya iniciado la validación.

Para adjuntar el depurador al proceso de validación, inserte una llamada a `System.Diagnostics.Debugger.Launch()` en el inicio del método de validación. Cuando aparezca el cuadro de diálogo depuración, seleccione la instancia principal de Visual Studio.

Alternativamente, puede insertar una llamada a `System.Windows.Forms.MessageBox.Show()`. Cuando aparezca el cuadro de mensaje, vaya a la instancia principal de Visual Studio y, en el menú **depurar** , haga clic en **asociar al proceso**. Seleccione el proceso denominado **Graphcmd.exe**.

Inicie siempre la instancia experimental presionando CTRL+F5 (**Iniciar sin depurar**).

### <a name="deploying-a-validation-extension"></a>Implementar una extensión de validación

Para instalar la extensión de validación en un equipo en el que está instalado una versión adecuada de Visual Studio, abra el archivo VSIX en el equipo de destino.

## <a name="example"></a> Example code

```csharp
using System;
using System.ComponentModel.Composition;
using System.Globalization;
using System.Linq;
using System.Text.RegularExpressions;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
using Microsoft.VisualStudio.GraphModel;

namespace Validator3
{
    [Export(typeof(IValidateArchitectureExtension))]
    public partial class Validator3Extension : IValidateArchitectureExtension
    {
        /// <summary>
        /// Validate the architecture
        /// </summary>
        /// <param name="graph">The graph</param>
        public void ValidateArchitecture(Graph graph)
        {
            if (graph == null) throw new ArgumentNullException("graph");

            // Uncomment the line below to debug this extension during validation
            // System.Windows.Forms.MessageBox.Show("Attach 2 to GraphCmd.exe with process id " + System.Diagnostics.Process.GetCurrentProcess().Id);

            // Get all layers on the diagram
            foreach (GraphNode layer in graph.Nodes.GetByCategory("Dsl.Layer"))
            {
                System.Threading.Thread.Sleep(100);
                // Get the required regex property from the layer node
                string regexPattern = "^[a-zA-Z]+$"; //layer[customPropertyCategory] as string;
                if (!string.IsNullOrEmpty(regexPattern))
                {
                    Regex regEx = new Regex(regexPattern);

                    // Get all referenced types in this layer including those from nested layers so each
                    // type is validated against all containing layer constraints.
                    foreach (GraphNode containedType in layer.FindDescendants().Where(node => node.HasCategory("CodeSchema_Type")))
                    {
                        // Check the type name against the required regex
                        CodeGraphNodeIdBuilder builder = new CodeGraphNodeIdBuilder(containedType.Id, graph);
                        string typeName = builder.Type.Name;
                        if (!regEx.IsMatch(typeName))
                        {
                            // Log an error
                            string message = string.Format(CultureInfo.CurrentCulture, Resources.InvalidTypeNameMessage, typeName);
                            this.LogValidationError(graph, typeName + "TypeNameError", message, GraphErrorLevel.Error, layer);
                        }
                    }
                }

            }

        }
    }
}
```

## <a name="see-also"></a>Vea también

- [Ampliación de diagramas de dependencia](../modeling/extend-layer-diagrams.md)
