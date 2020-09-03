---
title: 'Tutorial: analizar código administrado para los defectos de código | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, walkthroughs
- managed code, analyzing
- code analysis tool, walkthroughs
ms.assetid: 22b99f49-1924-4fb5-a421-c8b23e5d5cd4
caps.latest.revision: 47
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9478394162051fc08c33047cf1ac24275aff75e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72609334"
---
# <a name="walkthrough-analyzing-managed-code-for-code-defects"></a>Tutorial: Analizar código administrado en previsión de defectos de código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tutorial, se analiza un proyecto administrado para detectar defectos de código mediante la herramienta de análisis de código.

 Este tutorial le guiará a través del proceso de uso del análisis de código para analizar los ensamblados de código administrado de .NET según las directrices de diseño de Microsoft .NET Framework.

 En este tutorial realizará lo siguiente:

- Analice y corrija las advertencias de defectos de código.

## <a name="prerequisites"></a>Requisitos previos

- [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].

## <a name="create-a-class-library"></a>Creación de una biblioteca de clases

#### <a name="to-create-a-class-library"></a>Para crear una biblioteca de clases

1. En el menú **archivo** de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] , haga clic en **nuevo** y, a continuación, haga clic en **proyecto**.

2. En el cuadro de diálogo **nuevo proyecto** , en **tipos de proyecto**, haga clic en **Visual C#**.

3. En **Plantillas**, seleccione **Biblioteca de clases**.

4. En el cuadro de texto **nombre** , escriba **CodeAnalysisManagedDemo** y, a continuación, haga clic en **Aceptar**.

5. Una vez creado el proyecto, abra el archivo Class1.cs.

6. Reemplace el texto existente en Class1.cs por el código siguiente:

     `//CodeAnalysisManagedDemo //Class1.cs using System;  namespace testCode {          public class demo : Exception     {                  public static void Initialize(int size) { }         protected static readonly int _item;         public static int item { get { return _item; } }     } }`

7. Guarde el archivo Class1.cs.

## <a name="analyze-the-project"></a>Analizar el proyecto

#### <a name="to-analyze-a-managed-project-for-code-defects"></a>Para analizar un proyecto administrado para detectar defectos de código

1. Seleccione el proyecto CodeAnalysisManagedDemo en **Explorador de soluciones**.

2. En el menú **Proyecto** , haga clic en **Propiedades**.

     Se muestra la página de propiedades CodeAnalysisManagedDemo.

3. Haga clic en **CodeAnalysis**.

4. Asegúrese de que la opción  **Habilitar análisis de código al compilar (define CODE_ANALYSIS constante**) está activada.

5. En la lista desplegable **ejecutar este conjunto de reglas** , seleccione **Microsoft All Rules (todas las reglas**).

6. En el menú **archivo** , haga clic en **guardar los elementos seleccionados**y, a continuación, cierre las páginas de propiedades de ManagedDemo.

7. En el menú **compilar** , haga clic en **generar ManagedDemo**.

     Las advertencias de compilación del proyecto CodeAnalysisManagedDemo se muestran en las ventanas **análisis de código** y **salida** .

     Si no aparece la ventana **análisis de código** , en el menú **analizar** , elija **ventanas** y, a continuación, **Elija Análisis de código**.

## <a name="correct-the-code-analysis-issues"></a>Corregir los problemas de análisis de código

#### <a name="to-correct-code-analysis-rule-violations"></a>Para corregir las infracciones de reglas de análisis de código

1. En el menú **Ver** , haga clic en **Lista de errores**.

     Según el perfil de desarrollador que elija, puede que tenga que señalar a **otras ventanas** en el menú **Ver** y, a continuación, hacer clic en **lista de errores**.

2. En **Explorador de soluciones**, haga clic en **Mostrar todos los archivos**.

3. A continuación, expanda el nodo propiedades y, a continuación, abra el archivo AssemblyInfo.cs.

4. Use lo siguiente para corregir las advertencias:

- [CA1014: Marque los ensamblados con CLSCompliantAttribute](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft. Design: ' demo ' debe marcarse con CLSCompliantAttribute y su valor debe ser true.

  - Agregue el código `using``System;` al archivo AssemblyInfo.cs.

       A continuación, agregue el código `[assembly: CLSCompliant(true)]` al final del archivo AssemblyInfo.cs.

       Recompile el proyecto.

- [CA1032: implementar constructores de excepción estándar](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: agregue el siguiente constructor a esta clase: demo pública (cadena)

  - Agregue el constructor `public demo (String s) : base(s) { }` a la clase `demo` .

- [CA1032: implementar constructores de excepción estándar](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: agregue el siguiente constructor a esta clase: demo pública (cadena, excepción)

  - Agregue el constructor `public demo (String s, Exception e) : base(s, e) { }` a la clase `demo` .

- [CA1032: implementar constructores de excepción estándar](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: agregue el siguiente constructor a esta clase: demo protegida (SerializationInfo, StreamingContext)

  - Agregue el código `using System.Runtime.Serialization;` al principio del archivo Class1.cs.

       A continuación, agregue el constructor `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`

       Recompile el proyecto.

- [CA1032: implementar constructores de excepción estándar](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft. Design: agregue el siguiente constructor a esta clase: demo pública ()

  - Agregue el constructor `public demo () : base() { }` a la clase `demo` **.**

       Recompile el proyecto.

- [CA1709: los identificadores deben tener mayúsculas y minúsculas correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft. naming: corrija el uso de mayúsculas y minúsculas del nombre de espacio de nombres ' TestCode ' cambiándolo a ' TestCode '.

  - Cambie el uso de mayúsculas y minúsculas del espacio de nombres `testCode` a `TestCode` .

- [CA1709: los identificadores deben usarse correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft. naming: corrija el uso de mayúsculas y minúsculas del nombre de tipo ' demo ' cambiándolo a ' demo '.

  - Cambie el nombre del miembro a `Demo` .

- [CA1709: los identificadores deben tener mayúsculas y minúsculas correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft. naming: corrija el uso de mayúsculas y minúsculas del nombre de miembro ' item ' cambiándolo a ' item '.

  - Cambie el nombre del miembro a `Item` .

- [CA1710: los identificadores deberían tener el sufijo correcto](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Microsoft. naming: Rename ' TestCode. demo ' para terminar en ' Exception '.

  - Cambie el nombre de la clase y sus constructores a `DemoException` .

- [CA2210: los ensamblados deben tener nombres seguros válidos](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md): signo ' ManagedDemo ' con una clave de nombre seguro.

  - En el menú **proyecto** , haga clic en **propiedades de ManagedDemo**.

       Aparecen las propiedades del proyecto.

       Haga clic en **firma**.

       Active la casilla **firmar el ensamblado** .

       En la lista **elegir un archivo de clave de nombre de cadena** , seleccione **\<New…>** .

       Aparecerá el cuadro de diálogo **Crear clave de nombre seguro**.

       En el **nombre del archivo de clave**, escriba TestKey.

       Escriba una contraseña y haga clic en **Aceptar**.

       En el menú **archivo** , haga clic en **guardar los elementos seleccionados**y, a continuación, cierre las páginas de propiedades.

       Recompile el proyecto.

- [CA2237: Marque los tipos ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft. Usage: Agregue un atributo [Serializable] al tipo ' demo ', ya que este tipo implementa ISerializable.

  - Agregue el `[Serializable ()]` atributo a la clase `demo` .

       Recompile el proyecto.

  Después de completar los cambios, el archivo Class1.cs debe tener un aspecto similar al siguiente:

```
//CodeAnalysisManagedDemo
//Class1.cs
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

## <a name="exclude-code-analysis-warnings"></a>Excluir advertencias de análisis de código

#### <a name="to-exclude-code-defect-warnings"></a>Para excluir las advertencias de defectos de código

1. Para cada una de las advertencias restantes, haga lo siguiente:

   1. En la ventana Análisis de código, seleccione la advertencia.

   2. Elija **acciones**, elija **suprimir mensaje**y, a continuación, elija **en archivo de supresión del proyecto**.

      Para obtener más información, consulte [Cómo: suprimir advertencias mediante el elemento de menú.](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)

2. Recompile el proyecto.

    El proyecto se compila sin advertencias ni errores.
