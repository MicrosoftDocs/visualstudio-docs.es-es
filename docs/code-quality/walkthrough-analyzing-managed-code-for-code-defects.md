---
title: Tutorial analizar código administrado en previsión de defectos de código | Microsoft Docs
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
ms.openlocfilehash: 3a2ce9b719f77377abf5b2bebd81b03a2606258b
ms.sourcegitcommit: fd5a5b057df3d733f5224c305096907989811f85
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/18/2019
ms.locfileid: "67195301"
---
# <a name="walkthrough-use-static-code-analysis-to-find-code-defects"></a>Tutorial: Use el análisis de código estático para encontrar defectos de código

En este tutorial, analizaremos un proyecto administrado en previsión de defectos de código mediante la herramienta de análisis de código.

En este tutorial le guiará por el proceso de uso de análisis de código estático para analizar los ensamblados de código administrado de .NET de conformidad con las instrucciones de diseño. NET.

## <a name="create-a-class-library"></a>Crear una biblioteca de clases

### <a name="to-create-a-class-library"></a>Para crear una biblioteca de clases

1. En el menú **Archivo**, seleccione **Nuevo** > **Proyecto**.

1. En el **nuevo proyecto** cuadro de diálogo, expanda **instalado** > **Visual C#** y, a continuación, elija **Windows Desktop**.

1. Elija la **biblioteca de clases (.NET Framework)** plantilla.

1. En el **nombre** cuadro de texto, escriba **CodeAnalysisManagedDemo** y, a continuación, haga clic en **Aceptar**.

1. Una vez creado el proyecto, abra el *Class1.cs* archivo.

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

### <a name="to-analyze-a-managed-project-for-code-defects"></a>Para analizar un proyecto administrado en previsión de defectos de código

1. Seleccione el proyecto CodeAnalysisManagedDemo en **el Explorador de soluciones**.

1. En el menú **Proyecto**, haga clic en **Propiedades**.

     Se abrirá la página de propiedades de CodeAnalysisManagedDemo.

1. Elija la **análisis de código** ficha.

1. Asegúrese de que **Habilitar análisis de código al compilar** está activada.

1. Desde el **ejecutar este conjunto de reglas** lista desplegable, seleccione **todas las reglas de Microsoft**.

1. En el **archivo** menú, haga clic en **guardar los elementos seleccionados**y, a continuación, cierre las páginas de propiedades.

1. En el **compilar** menú, haga clic en **CodeAnalysisManagedDemo compilar**.

    En el que se muestran las advertencias de compilación del proyecto CodeAnalysisManagedDemo el **lista de errores** y **salida** windows.

## <a name="correct-the-code-analysis-issues"></a>Corrija los problemas de análisis de código

### <a name="to-correct-code-analysis-rule-violations"></a>Para corregir las infracciones de reglas de análisis de código

1. En el **vista** menú, elija **lista de errores**.

    Según el perfil de desarrollador que haya elegido, puede tener para que apunte a **Other Windows** en el **vista** menú y, a continuación, elija **lista de errores**.

1. En el **Explorador de soluciones**, elija **Mostrar todos los archivos**.

1. Expanda el nodo de propiedades y, a continuación, abra el *AssemblyInfo.cs* archivo.

1. Utilice las siguientes sugerencias para corregir las advertencias:

   [CA1014: Marque los ensamblados con CLSCompliantAttribute](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft.Design: 'demo' debe marcarse con el atributo CLSCompliantAttribute y su valor debe ser true.

   1. Agregue el código `using System;` al archivo AssemblyInfo.cs.

   1. A continuación, agregue el código `[assembly: CLSCompliant(true)]` hasta el final del archivo AssemblyInfo.cs.

   [CA1032: Implementar constructores de excepción estándar](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Agregue el siguiente constructor a esta clase: public demo (String)

   1. Agregue el constructor `public demo (String s) : base(s) { }` a la clase `demo`.

   [CA1032: Implementar constructores de excepción estándar](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Agregue el siguiente constructor a esta clase: public demo (String, Exception)

   1. Agregue el constructor `public demo (String s, Exception e) : base(s, e) { }` a la clase `demo`.

   [CA1032: Implementar constructores de excepción estándar](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Agregue el siguiente constructor a esta clase: protected demo (SerializationInfo, StreamingContext)

   1. Agregue el código `using System.Runtime.Serialization;` al principio del archivo Class1.cs.

   1. A continuación, agregue el constructor `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`

   [CA1032: Implementar constructores de excepción estándar](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Agregue el siguiente constructor a esta clase: public demo()

   1. Agregue el constructor `public demo () : base() { }` a la clase `demo` **.**

   [CA1709: Los identificadores deberían escribirse correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Corrija el uso de mayúsculas y minúsculas del nombre de espacio de nombres 'testCode' cambiándolo a 'TestCode'.

   1. Cambiar las mayúsculas y minúsculas del espacio de nombres `testCode` a `TestCode`.

   [CA1709: Los identificadores deberían escribirse correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Corrija el uso de mayúsculas y minúsculas de demostración' nombre de tipo' cambiándolo a 'Demo'.

   1. Cambiar el nombre del miembro que `Demo`.

   [CA1709: Los identificadores deberían escribirse correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: Corrija el uso de mayúsculas y minúsculas del miembro nombre 'item' cambiándolo a 'Item'.

   1. Cambiar el nombre del miembro que `Item`.

   [CA1710: Los identificadores deberían tener el sufijo correcto](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Microsoft.Naming: Cambie el nombre 'testCode.demo' final 'Excepción'.

   1. Cambiar el nombre de la clase y sus constructores para `DemoException`.

   [CA2210: Los ensamblados deben tener nombres seguros válidos](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md): Firmar 'CodeAnalysisManagedDemo' con una clave de nombre seguro.

   1. En el **proyecto** menú, elija **CodeAnalysisManagedDemo propiedades**.

      Aparecen las propiedades del proyecto.

   1. Elija la pestaña **Firma** .

   1. Seleccione el **firmar el ensamblado** casilla de verificación.

   1. En el **elegir un archivo de clave de nombre de cadena** lista, seleccione  **\<nuevo... >** .

      El **crear clave de nombre seguro** aparece el cuadro de diálogo.

   1. En el **nombre de archivo de clave**, escriba TestKey.

   1. Escriba una contraseña y, a continuación, elija **Aceptar**.

   1. En el **archivo** menú, elija **guardar los elementos seleccionados**y, a continuación, cierre las páginas de propiedades.

   [CA2237: Marcar los tipos ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft.Usage: Agregue un atributo [Serializable] al tipo 'demo' ya que este tipo implementa ISerializable.

   1. Agregar el `[Serializable ()]` a la clase `demo`.

   Una vez completados los cambios, el archivo Class1.cs debe ser similar al siguiente:

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

## <a name="exclude-code-analysis-warnings"></a>Excluya las advertencias de análisis de código

1. Para cada una de las advertencias restantes, realice lo siguiente:

    1. Seleccione la advertencia en el **lista de errores**.

    1. En el menú contextual (menú contextual), elija **suprimir** > **en el archivo de supresión**.

1. Recompile el proyecto.

     El proyecto se compila sin errores ni advertencias.

## <a name="see-also"></a>Vea también

[Análisis de código para código administrado](../code-quality/code-analysis-for-managed-code-overview.md)