---
title: Tutorial análisis del código administrado para defectos de código | Microsoft Docs
ms.date: 01/29/2018
ms.topic: conceptual
helpviewer_keywords:
- code analysis [Visual Studio]
- managed code, analyzing
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ab1e0b890d6241742770ed38ff61fc1c2c0ed2f4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72535693"
---
# <a name="walkthrough-use-static-code-analysis-to-find-code-defects"></a>Tutorial: usar el análisis de código estático para buscar defectos de código

En este tutorial, analizará un proyecto administrado para detectar defectos de código mediante el análisis de código heredado.

Este artículo le guiará a través del proceso de uso del análisis heredado para analizar los ensamblados de código administrado de .NET para que cumplan las directrices de diseño de .NET.

## <a name="create-a-class-library"></a>Creación de una biblioteca de clases

1. Abra Visual Studio y cree un nuevo proyecto a partir de la plantilla de **biblioteca de clases (.NET Framework)** .

1. Asigne al proyecto el nombre **CodeAnalysisManagedDemo**.

1. Una vez creado el proyecto, abra el archivo *Class1.CS* .

1. Reemplace el texto existente en Class1.cs por el código siguiente:

   ```csharp
   using System;

   namespace testCode
   {
       public class demo : Exception
       {
           public static void Initialize(int size) { }
           protected static readonly int _item;
           public static int item { get { return _item; } }
       }
   }
   ```

1. Guarde el archivo Class1.cs.

## <a name="analyze-the-project-for-code-defects"></a>Analizar el proyecto para detectar defectos de código

1. Seleccione el proyecto CodeAnalysisManagedDemo en **Explorador de soluciones**.

2. En el menú **Proyecto** , haga clic en **Propiedades**.

   Se muestra la página de propiedades CodeAnalysisManagedDemo.

3. Elija la pestaña **análisis de código** .

::: moniker range="vs-2017"

4. Asegúrese de que está seleccionada la opción **Habilitar análisis de código al compilar** .

5. En la lista desplegable **ejecutar este conjunto de reglas** , seleccione **Microsoft All Rules (todas las reglas**).

::: moniker-end

::: moniker range=">=vs-2019"

4. Asegúrese de que la opción **ejecutar al compilar** está seleccionada en la sección **analizadores binarios** .

5. En la lista desplegable **reglas activas** , seleccione **Microsoft All Rules (todas las reglas**).

::: moniker-end

6. En el menú **archivo** , haga clic en **guardar los elementos seleccionados**y, a continuación, cierre las páginas de propiedades.

7. En el menú **compilar** , haga clic en **generar CodeAnalysisManagedDemo**.

    Las advertencias de compilación del proyecto CodeAnalysisManagedDemo se muestran en las ventanas **lista de errores** y **salida** .

## <a name="correct-the-code-analysis-issues"></a>Corregir los problemas de análisis de código

1. En el menú **Ver** , elija **lista de errores**.

    Según el perfil de desarrollador que elija, puede que tenga que señalar a **otras ventanas** en el menú **Ver** y, a continuación, elegir **lista de errores**.

1. En el **Explorador de soluciones**, elija **Mostrar todos los archivos**.

1. Expanda el nodo propiedades y, a continuación, abra el archivo *AssemblyInfo.CS* .

1. Use las siguientes sugerencias para corregir las advertencias:

   [CA1014: Marque los ensamblados con CLSCompliantAttribute](../code-quality/ca1014.md): agregue el código `[assembly: CLSCompliant(true)]` al final del archivo AssemblyInfo.cs.

   [CA1032: implementar constructores de excepción estándar](../code-quality/ca1032.md): agregue el constructor `public demo (String s) : base(s) { }` a la clase `demo` .

   [CA1032: implementar constructores de excepción estándar](../code-quality/ca1032.md): agregue el constructor `public demo (String s, Exception e) : base(s, e) { }` a la clase `demo` .

   [CA1032: implementar constructores de excepción estándar](../code-quality/ca1032.md): agregue el constructor `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { }` a la clase demo. También deberá agregar una `using` instrucción para <xref:System.Runtime.Serialization?displayProperty=fullName> .

   [CA1032: implementar constructores de excepción estándar](../code-quality/ca1032.md): agregue el constructor `public demo () : base() { }` a la clase `demo` .

   [CA1709: los identificadores deben usar mayúsculas y minúsculas correctamente](../code-quality/ca1709.md): cambie el uso de mayúsculas y minúsculas del espacio de nombres `testCode` a `TestCode` .

   [CA1709: los identificadores deben usar mayúsculas y minúsculas correctamente](../code-quality/ca1709.md): cambie el nombre del miembro a `Demo` .

   [CA1709: los identificadores deben usar mayúsculas y minúsculas correctamente](../code-quality/ca1709.md): cambie el nombre del miembro a `Item` .

   [CA1710: los identificadores deberían tener el sufijo correcto](../code-quality/ca1710.md): cambie el nombre de la clase y sus constructores a `DemoException` .

   [CA2237: Marque los tipos ISerializable con SerializableAttribute](../code-quality/ca2237.md): agregue el `[Serializable ()]` atributo a la clase `demo` .

   [CA2210: los ensamblados deben tener nombres seguros válidos](../code-quality/ca2210.md): signo ' CodeAnalysisManagedDemo ' con una clave de nombre seguro:

   1. En el menú **proyecto** , elija **propiedades de CodeAnalysisManagedDemo**.

      Aparecen las propiedades del proyecto.

   1. Elija la pestaña **Firma** .

   1. Active la casilla **firmar el ensamblado** .

   1. En la lista **elegir un archivo de clave de nombre de cadena** , seleccione **\<New>** .

      Aparecerá el cuadro de diálogo **Crear clave de nombre seguro**.

   1. En **nombre de archivo de clave**, escriba **TestKey**.

   1. Escriba una contraseña y, después, elija **Aceptar**.

   1. En el menú **archivo** , elija **Guardar elementos seleccionados**y, a continuación, cierre las páginas de propiedades.

   Después de completar todos los cambios, el archivo Class1.cs debe tener un aspecto similar al siguiente:

   ```csharp
   using System;
   using System.Runtime.Serialization;

   namespace TestCode
   {
       [Serializable()]
       public class DemoException : Exception
       {
           public DemoException () : base() { }
           public DemoException(String s) : base(s) { }
           public DemoException(String s, Exception e) : base(s, e) { }
           protected DemoException(SerializationInfo info, StreamingContext context) : base(info, context) { }

           public static void Initialize(int size) { }
           protected static readonly int _item;
           public static int Item { get { return _item; } }
       }
   }
   ```

1. Recompile el proyecto.

## <a name="exclude-code-analysis-warnings"></a>Excluir advertencias de análisis de código

1. Para cada una de las advertencias restantes, haga lo siguiente:

    1. Seleccione la advertencia en el **lista de errores**.

    1. En el menú contextual, elija **suprimir**  >  **en archivo de supresión**.

1. Recompile el proyecto.

     El proyecto se compila sin advertencias ni errores.

## <a name="see-also"></a>Consulte también

[Análisis de código para código administrado](../code-quality/code-analysis-for-managed-code-overview.md)
