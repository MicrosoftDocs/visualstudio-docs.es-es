---
title: "Tutorial: Analizar código administrado en previsión de defectos de código | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code analysis, walkthroughs
- managed code, analyzing
- code analysis tool, walkthroughs
ms.assetid: 22b99f49-1924-4fb5-a421-c8b23e5d5cd4
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 6ea39704ea232fb304257b897087f0ae60d19c4f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-analyzing-managed-code-for-code-defects"></a>Tutorial: Analizar código administrado en previsión de defectos de código
En este tutorial, analizar un proyecto administrado en previsión de defectos de código mediante la herramienta de análisis de código.  
  
 Este tutorial le guiará a través del proceso de uso de análisis de código para analizar los ensamblados de código administrado de .NET de conformidad con las directrices de diseño de Microsoft .NET Framework.  
  
 En este tutorial,:  
  
-   Analizar y corregir las advertencias de defectos de código.  
  
## <a name="prerequisites"></a>Requisitos previos  
  
-   [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)].  
  
## <a name="create-a-class-library"></a>Crear una biblioteca de clases  
  
#### <a name="to-create-a-class-library"></a>Para crear una biblioteca de clases  
  
1.  En el **archivo** menú de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], haga clic en **New** y, a continuación, haga clic en **proyecto**.  
  
2.  En el **nuevo proyecto** cuadro de diálogo **tipos de proyecto**, haga clic en **Visual C#**.  
  
3.  En **plantillas**, seleccione **biblioteca de clases**.  
  
4.  En el **nombre** cuadro de texto, escriba **CodeAnalysisManagedDemo** y, a continuación, haga clic en **Aceptar**.  
  
5.  Una vez creado el proyecto, abra el archivo Class1.cs.  
  
6.  Reemplace el texto existente en Class1.cs con el código siguiente:  
  
     `//CodeAnalysisManagedDemo //Class1.cs using System;  namespace testCode {          public class demo : Exception     {                  public static void Initialize(int size) { }         protected static readonly int _item;         public static int item { get { return _item; } }     } }`  
  
7.  Guarde el archivo Class1.cs.  
  
## <a name="analyze-the-project"></a>Analizar el proyecto  
  
#### <a name="to-analyze-a-managed-project-for-code-defects"></a>Para analizar un proyecto administrado en previsión de defectos de código  
  
1.  Seleccione el proyecto CodeAnalysisManagedDemo en **el Explorador de soluciones**.  
  
2.  En el menú **Proyecto**, haga clic en **Propiedades**.  
  
     Se abrirá la página de propiedades de CodeAnalysisManagedDemo.  
  
3.  Haga clic en **CodeAnalysis**.  
  
4.  Asegúrese de que **Habilitar análisis de código al compilar (define la constante CODE_ANALYSIS**) está activada.  
  
5.  Desde el **ejecutar este conjunto de reglas** lista desplegable, seleccione **todas las reglas de Microsoft**.  
  
6.  En el **archivo** menú, haga clic en **guardar los elementos seleccionados**y, a continuación, cierre las páginas de propiedades de ManagedDemo.  
  
7.  En el **generar** menú, haga clic en **Generar ManagedDemo**.  
  
     Las advertencias de compilación del proyecto CodeAnalysisManagedDemo se notifican en la **análisis de código** y **salida** windows.  
  
     Si el **análisis de código** ventana no aparece, en la **analizar** menú, elija **Windows** y, a continuación, **elija análisis de código**.  
  
## <a name="correct-the-code-analysis-issues"></a>Corregir los problemas de análisis de código  
  
#### <a name="to-correct-code-analysis-rule-violations"></a>Para corregir las infracciones de reglas de análisis de código  
  
1.  En el **vista** menú, haga clic en **lista de errores**.  
  
     Dependiendo del perfil del desarrollador que eligió, es posible que deba hacer **otras ventanas** en el **vista** menú y, a continuación, haga clic en **lista de errores**.  
  
2.  En **el Explorador de soluciones**, haga clic en **mostrar todos los archivos**.  
  
3.  A continuación, expanda el nodo propiedades y, a continuación, abra el archivo AssemblyInfo.cs.  
  
4.  Para corregir las advertencias, utilice lo siguiente:  
  
-   [CA1014: Marcar los ensamblados con CLSCompliantAttribute](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft.Design: 'demo' debe marcarse con CLSCompliantAttribute y su valor debe ser true.  
  
    -   Agregue el código `using``System;` al archivo AssemblyInfo.cs.  
  
         A continuación, agregue el código `[assembly: CLSCompliant(true)]` hasta el final del archivo AssemblyInfo.cs.  
  
         Recompile el proyecto.  
  
-   [CA1032: Implementar constructores de excepción estándar](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: agregue el siguiente constructor a esta clase: public demo (String)  
  
    -   Agregue el constructor `public demo (String s) : base(s) { }` a la clase `demo`.  
  
-   [CA1032: Implementar constructores de excepción estándar](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: agregue el siguiente constructor a esta clase: public demo (String, Exception)  
  
    -   Agregue el constructor `public demo (String s, Exception e) : base(s, e) { }` a la clase `demo`.  
  
-   [CA1032: Implementar constructores de excepción estándar](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: agregue el siguiente constructor a esta clase: protected demo (SerializationInfo, StreamingContext)  
  
    -   Agregue el código `using System.Runtime.Serialization;` al principio del archivo Class1.cs.  
  
         A continuación, agregue el constructor`protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`  
  
         Recompile el proyecto.  
  
-   [CA1032: Implementar constructores de excepción estándar](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: agregue el siguiente constructor a esta clase: public demo()  
  
    -   Agregue el constructor `public demo () : base() { }` a la clase `demo` **.**  
  
         Recompile el proyecto.  
  
-   [CA1709: Los identificadores deben ser minúsculas correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: corrija las mayúsculas y minúsculas del nombre de espacio de nombres 'testCode' cambiándolo a 'TestCode'.  
  
    -   Cambiar las mayúsculas y minúsculas del espacio de nombres `testCode` a `TestCode`.  
  
-   [CA1709: Los identificadores deben ser minúsculas correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: corrija las mayúsculas y minúsculas de tipo nombre 'demo' cambiándolo a 'Demo'.  
  
    -   Cambiar el nombre del miembro que `Demo`.  
  
-   [CA1709: Los identificadores deben ser minúsculas correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: corrija las mayúsculas y minúsculas del miembro nombre 'item' cambiándolo a 'Item'.  
  
    -   Cambiar el nombre del miembro que `Item`.  
  
-   [CA1710: Los identificadores deberían tener el sufijo correcto](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Microsoft.Naming: cambiar el nombre 'testCode.demo' para que termine en 'Exception'.  
  
    -   Cambiar el nombre de la clase y sus constructores `DemoException`.  
  
-   [CA2210: Los ensamblados deben tener nombres seguros válidos](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md): firme 'ManagedDemo' con una clave de nombre seguro.  
  
    -   En el **proyecto** menú, haga clic en **ManagedDemo propiedades**.  
  
         Aparecen las propiedades del proyecto.  
  
         Haga clic en **firma**.  
  
         Seleccione el **firmar el ensamblado** casilla de verificación.  
  
         En el **elegir un archivo de clave de nombre de cadena** lista, seleccione  **\<nuevo... >**.  
  
         El **crear clave de nombre seguro** aparece el cuadro de diálogo.  
  
         En el **nombre de archivo de clave**, escriba TestKey.  
  
         Escriba una contraseña y, a continuación, haga clic en **Aceptar**.  
  
         En el **archivo** menú, haga clic en **guardar los elementos seleccionados**y, a continuación, cierre las páginas de propiedades.  
  
         Recompile el proyecto.  
  
-   [CA2237: Marcar los tipos ISerializable con SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft.Usage: agregar un atributo [Serializable] al tipo 'demo' ya que este tipo implementa ISerializable.  
  
    -   Agregar el `[Serializable ()]` a la clase de atributo `demo`.  
  
         Recompile el proyecto.  
  
 Después de completar los cambios, el archivo Class1.cs debe ser similar al siguiente:  
  
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
  
## <a name="exclude-code-analysis-warnings"></a>Excluya las advertencias de análisis de código  
  
#### <a name="to-exclude-code-defect-warnings"></a>Para excluir las advertencias de defectos de código  
  
1.  Para cada una de las advertencias restantes, haga lo siguiente:  
  
    1.  En la ventana de análisis de código, seleccione la advertencia.  
  
    2.  Elija **acciones**, a continuación, elija **suprimir mensaje**y, a continuación, elija **en el archivo de supresión de proyecto**.  
  
     Para obtener más información, vea [Cómo: Suprimir advertencias mediante el elemento de menú](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)  
  
2.  Recompile el proyecto.  
  
     El proyecto se compila sin errores ni advertencias.