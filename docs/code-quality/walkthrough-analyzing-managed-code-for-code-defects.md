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
ms.openlocfilehash: 4a00fdb2a41a03554113f2ecb626185aab2c74d5
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69548001"
---
# <a name="walkthrough-use-static-code-analysis-to-find-code-defects"></a>Tutorial: Usar el análisis de código estático para buscar defectos de código

En este tutorial, analizará un proyecto administrado para detectar defectos de código mediante el análisis de código heredado.

Este artículo le guiará a través del proceso de uso del análisis heredado para analizar los ensamblados de código administrado de .NET para que cumplan las directrices de diseño de .NET.

## <a name="create-a-class-library"></a>Crear una biblioteca de clases

### <a name="to-create-a-class-library"></a>Para crear una biblioteca de clases

1. En el menú **Archivo**, seleccione **Nuevo** > **Proyecto**.

1. En el cuadro de diálogo **nuevo proyecto** , expanda **instalado** > **C#visual**y, a continuación, elija **escritorio de Windows**.

1. Elija la plantilla **biblioteca de clases (.NET Framework)** .

1. En el cuadro de texto **nombre** , escriba **CodeAnalysisManagedDemo** y, a continuación, haga clic en **Aceptar**.

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

## <a name="analyze-the-project"></a>Analizar el proyecto

### <a name="to-analyze-a-managed-project-for-code-defects"></a>Para analizar un proyecto administrado para detectar defectos de código

1. Seleccione el proyecto CodeAnalysisManagedDemo en **Explorador de soluciones**.

1. En el menú **Proyecto**, haga clic en **Propiedades**.

     Se muestra la página de propiedades CodeAnalysisManagedDemo.

1. Elija la pestaña **análisis de código** .

1. Asegúrese de que la opción **Habilitar análisis de código al** compilar está activada.

1. En la lista desplegable **ejecutar este conjunto de reglas** , seleccione **Microsoft All Rules (todas las reglas**).

1. En el menú **archivo** , haga clic en **guardar los elementos seleccionados**y, a continuación, cierre las páginas de propiedades.

1. En el menú compilar, haga clic en **generar CodeAnalysisManagedDemo**.

    Las advertencias de compilación del proyecto CodeAnalysisManagedDemo se muestran en las ventanas **lista de errores** y **salida** .

## <a name="correct-the-code-analysis-issues"></a>Corregir los problemas de análisis de código

### <a name="to-correct-code-analysis-rule-violations"></a>Para corregir las infracciones de reglas de análisis de código

1. En el menú **Ver** , elija **lista de errores**.

    Según el perfil de desarrollador que elija, puede que tenga que señalar a **otras ventanas** en el menú **Ver** y, a continuación, elegir **lista de errores**.

1. En el **Explorador de soluciones**, elija **Mostrar todos los archivos**.

1. Expanda el nodo propiedades y, a continuación, abra el archivo *AssemblyInfo.CS* .

1. Use las siguientes sugerencias para corregir las advertencias:

   [CA1014: Marque los ensamblados](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)con CLSCompliantAttribute: Microsoft. Design: ' demo ' se debe marcar con CLSCompliantAttribute y su valor debe ser true.

   1. Agregue el código `using System;` al archivo AssemblyInfo.cs.

   1. A continuación, agregue el `[assembly: CLSCompliant(true)]` código al final del archivo AssemblyInfo.cs.

   [CA1032: Implementar constructores](../code-quality/ca1032-implement-standard-exception-constructors.md)de excepción estándar: Microsoft.Design: Agregue el siguiente constructor a esta clase: Public demo (cadena)

   1. Agregue el constructor `public demo (String s) : base(s) { }` a la clase `demo`.

   [CA1032: Implementar constructores](../code-quality/ca1032-implement-standard-exception-constructors.md)de excepción estándar: Microsoft.Design: Agregue el siguiente constructor a esta clase: Public demo (cadena, excepción)

   1. Agregue el constructor `public demo (String s, Exception e) : base(s, e) { }` a la clase `demo`.

   [CA1032: Implementar constructores](../code-quality/ca1032-implement-standard-exception-constructors.md)de excepción estándar: Microsoft.Design: Agregue el siguiente constructor a esta clase: demo protegida (SerializationInfo, StreamingContext)

   1. Agregue el código `using System.Runtime.Serialization;` al principio del archivo Class1.cs.

   1. A continuación, agregue el constructor`protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`

   [CA1032: Implementar constructores](../code-quality/ca1032-implement-standard-exception-constructors.md)de excepción estándar: Microsoft.Design: Agregue el siguiente constructor a esta clase: demo pública ()

   1. Agregue el constructor `public demo () : base() { }` a la clase `demo` **.**

   [CA1709: Los identificadores deben tener mayúsculas](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)y minúsculas: Microsoft.Naming: Corrija el uso de mayúsculas y minúsculas del nombre de espacio de nombres ' testCode ' cambiándolo a ' TestCode '.

   1. Cambie el uso de mayúsculas `testCode` y `TestCode`minúsculas del espacio de nombres a.

   [CA1709: Los identificadores deben tener mayúsculas](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)y minúsculas: Microsoft.Naming: Corrija el uso de mayúsculas y minúsculas del nombre de tipo ' demo ' cambiándolo a ' demo '.

   1. Cambie el nombre del miembro a `Demo`.

   [CA1709: Los identificadores deben tener mayúsculas](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)y minúsculas: Microsoft.Naming: Corrija el uso de mayúsculas y minúsculas del nombre de miembro ' item ' cambiándolo a ' item '.

   1. Cambie el nombre del miembro a `Item`.

   [CA1710: Los identificadores deben tener el](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)sufijo correcto: Microsoft.Naming: Cambie el nombre de ' testCode. demo ' para que termine en ' Exception '.

   1. Cambie el nombre de la clase y sus constructores a `DemoException`.

   [CA2210 Los ensamblados deben tener nombres](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md)seguros válidos: Firme ' CodeAnalysisManagedDemo ' con una clave de nombre seguro.

   1. En el menú **proyecto** , elija **propiedades de CodeAnalysisManagedDemo**.

      Aparecen las propiedades del proyecto.

   1. Elija la pestaña **Firma** .

   1. Active la casilla **firmar el ensamblado** .

   1. En la lista **elegir un archivo de clave de nombre de cadena** , seleccione  **\<nuevo... >** .

      Aparecerá el cuadro de diálogo **crear clave de nombre seguro** .

   1. En el **nombre del archivo de clave**, escriba TestKey.

   1. Escriba una contraseña y, después, elija **Aceptar**.

   1. En el menú **archivo** , elija **Guardar elementos seleccionados**y, a continuación, cierre las páginas de propiedades.

   [CA2237: Marque tipos ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft.Usage: Agregue un atributo [Serializable] al tipo ' demo ', ya que este tipo implementa ISerializable.

   1. Agregue el `[Serializable ()]` atributo a la clase `demo`.

   Después de completar los cambios, el archivo Class1.cs debe tener un aspecto similar al siguiente:

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

    1. En el menú contextual, elija **suprimir** > **en archivo de supresión**.

1. Recompile el proyecto.

     El proyecto se compila sin advertencias ni errores.

## <a name="see-also"></a>Vea también

[Análisis de código para código administrado](../code-quality/code-analysis-for-managed-code-overview.md)