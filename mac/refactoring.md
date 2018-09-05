---
title: Refactorización de código
description: La reorganización del código en Visual Studio para Mac es muy sencilla mediante el análisis de código fuente.
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.openlocfilehash: 8652b73b9bd7e414a989a1b711238126a742290f
ms.sourcegitcommit: 2597236a481afbaf1ad4915743898ee1aee49760
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2018
ms.locfileid: "43224424"
---
# <a name="refactoring"></a>Refactorización

Mediante la refactorización del código, es posible reorganizar, reestructurar y aclarar el código existente garantizando que no cambie el comportamiento general del código.

La refactorización genera un código base más correcto, lo que lo hace mucho más utilizable, legible y fácil de mantener para cualquier desarrollador o usuario que haga referencia al código.

La integración de Visual Studio para Mac con Roslyn, la plataforma de compilador de .NET de código abierto de Microsoft, permite más operaciones de refactorización.

## <a name="renaming"></a>Cambiar nombre 

El comando de refactorización *Cambiar nombre* puede usarse en cualquier identificador de código (por ejemplo, un nombre de clase, un nombre de propiedad, etc.) para buscar todas las apariciones de ese identificador y cambiarlas. Para cambiar el nombre de un símbolo, haga clic con el botón derecho en él y elija **Refactorizar > Cambiar nombre**, o el enlace de teclado **Cmd + R**:

![Elemento de menú Cambiar nombre](media/refactoring-renaming1.png)

Esto resaltará el símbolo y todas las referencias a él. Cuando empiece a escribir un nuevo nombre, se cambiarán automáticamente todas las referencias en el código. Para indicar la finalización del proceso de cambiar nombre, pulse **ENTRAR**:

 ![Cambiar nombre e identificador](media/refactoring-renaming2.png)

## <a name="context-actions"></a>Acciones de contexto

Las acciones de contexto permiten inspeccionar código de C# y ver todas las opciones de refactorización posibles. 

Los elementos de contexto **Resolver** y **Refactorizar** se combinan en un solo elemento *Corrección rápida…* que proporciona todas las acciones de contexto disponibles:

![Mostrar elementos de contexto](media/refactoring-context-action.png)

Al mantener el puntero sobre las acciones de contexto aparecerá una vista previa de lo que se agregará o se quitará del código.

Como alternativa, puede pulsar **Opción + Entrar** en cualquier lugar del código:

![Elementos de contexto Opción + Entrar](media/refactoring-image2a.png)

Para habilitar estas opciones, debe seleccionar *Habilitar análisis de código fuente de archivos abiertos* en las opciones **Visual Studio para Mac > Preferencias > Editor de texto > Análisis de código fuente**:

 ![Habilitar análisis de código fuente](media/refactoring-options.png)

Se pueden sugerir más de 100 acciones. Para habilitarlas o deshabilitarlas, vaya a **Visual Studio para Mac > Preferencias > Análisis de código fuente > C# > Acciones de código** y active o desactive la casilla situada junto a la acción:

 ![Acciones de análisis de código fuente de C#](media/refactoring-image3a.png)

### <a name="common-context-actions"></a>Acciones de contexto comunes

A continuación se explican algunas de las acciones de contexto más usadas.

#### <a name="extract-method"></a>Extraer método

La operación de refactorización Extraer método permite crear un método al extraer una selección de código de un miembro existente. Esta acción hace dos cosas:

* Crea un método que contiene el código seleccionado.
* Llama al método nuevo en el lugar donde estaba el código seleccionado.

##### <a name="example"></a>Ejemplo

1. Agregue el código siguiente:

```csharp
    class MainClass
    {

        double CalculatePyramidVolume(double baseArea, double height)
        {

            double volume = (baseArea * height) / 3;

            return volume;
        }
    }
```

2. Resalte la línea `double volume = (baseArea * height) / 3;`, haga clic con el botón derecho en ella y seleccione **Refactorizar > Extraer método**.

3. Use las teclas de dirección para seleccionar dónde se debe colocar el nuevo método en el código.


#### <a name="encapsulate-field"></a>Encapsular campo

La operación Encapsular campo permite crear una propiedad a partir de un campo existente y actualiza el código para hacer referencia a la propiedad recién creada. Al crear una propiedad que encapsula el campo, no se permite el acceso directo al campo público, lo que significa que no lo pueden modificar otros objetos.

Esta acción hace lo siguiente:

* Cambia el modificador de acceso a privado.
* Genera un captador y un establecedor para el campo (a menos que el campo sea de solo lectura, en cuyo caso solo creará un captador).


## <a name="source-analysis"></a>Análisis de código fuente

El análisis de código fuente analiza el código sobre la marcha. Para ello, subraya los posibles errores e infracciones de estilo y proporciona correcciones automáticas como acciones de contexto. 

Para ver todos los resultados del análisis de código fuente de un archivo, observe la barra de desplazamiento a la derecha del editor de texto:

 ![Barra lateral del análisis de código fuente](media/refactoring-image4a.png)

Si hace clic en el círculo situado en la parte superior, puede iterar cada sugerencia. Los problemas con la gravedad más alta se muestran los primeros. Si mantiene el puntero sobre una línea o un resultado se mostrarán los problemas, que podrá corregir mediante las acciones de contexto:

 ![Elemento Análisis de código fuente](media/refactoring-image5.png)

