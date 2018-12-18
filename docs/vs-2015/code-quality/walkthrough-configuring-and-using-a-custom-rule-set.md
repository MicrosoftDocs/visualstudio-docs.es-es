---
title: 'Tutorial: Configurar y usar un personalizado en un conjunto de reglas | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code analysis, walkthroughs
- code analysis, rule sets
ms.assetid: 7fe0a4e3-1ce0-4f38-a87a-7d81238ec7cd
caps.latest.revision: 42
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5976ee0c0fbfc4befe97f2ab25c46744a8267134
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49906057"
---
# <a name="walkthrough-configuring-and-using-a-custom-rule-set"></a>Tutorial: Configurar y utilizar un conjunto de reglas personalizado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tutorial se muestra cómo usar las herramientas de análisis de código que se han configurado para utilizar una personalizada *conjunto de reglas* en una biblioteca de clases. Puede seleccionar un conjunto de reglas que se relaciona con el tipo de proyecto que ha especificado para la solución, o puede seleccionar otros conjuntos de reglas para satisfacer una necesidad concreta, como la exploración de código heredado para los problemas que se pueden corregir de una manera sin interrupción. En cualquier caso, los conjuntos de reglas también se pueden personalizar para ajustar a los requisitos del proyecto.  
  
 En este tutorial, llevará a cabo estos procesos:  
  
-   Crear una biblioteca de clases.  
  
-   Seleccione el **reglas de directrices de diseño básicas de Microsoft** conjunto de reglas de análisis de código.  
  
-   Agregue su propio código a la clase.  
  
-   Ejecutar análisis de código.  
  
-   Personalizar el conjunto de reglas.  
  
-   Ejecutar análisis de código y ver cómo funciona el comportamiento personalización ha definido la regla.  
  
## <a name="prerequisites"></a>Requisitos previos  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]o [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
## <a name="using-rule-sets-with-code-analysis"></a>Usar conjuntos de reglas con análisis de código  
 En primer lugar, cree una biblioteca de clases simple.  
  
#### <a name="create-a-class-library"></a>Crear una biblioteca de clases  
  
1. En el menú **Archivo** , haga clic en **Nuevo** y, a continuación, haga clic en **Proyecto**.  
  
2. En el **nuevo proyecto** cuadro de diálogo **tipos de proyecto**, haga clic en **Visual C#**.  
  
3. En **Visual C#**, seleccione **biblioteca de clases**.  
  
4. En el **nombre** cuadro de texto, escriba **RuleSetSample** y, a continuación, haga clic en **Aceptar**.  
  
   A continuación, seleccionará el **reglas de directrices de diseño básicas de Microsoft** conjunto de reglas y guárdelo con el proyecto.  
  
#### <a name="select-a-code-analysis-rule-set"></a>Seleccione un conjunto de reglas de análisis de código  
  
1. En el **analizar** menú, haga clic en **configurar análisis de código para RuleSetSample**.  
  
    Aparecen las opciones de configuración para el análisis de código.  
  
2. En el **ejecutar este conjunto de reglas** lista desplegable, seleccione **todas las reglas de Microsoft**.  
  
    Para obtener más información acerca de los conjuntos de reglas disponibles, consulte [referencia de conjunto de reglas de análisis de código](../code-quality/code-analysis-rule-set-reference.md).  
  
    En el menú archivo, haga clic en **guardar elementos seleccionados** para actualizar el archivo de proyecto con información sobre el conjunto de reglas que ha seleccionado y su configuración.  
  
   > [!TIP]
   >  En una situación real, una buena práctica que se usará para dar prioridad a qué problemas desea dirigir con análisis de código es comenzar con la **reglas mínimas recomendadas** conjunto de reglas y corregir los problemas deseados y, a continuación, agregar de forma incremental más reglas o la regla se establece para encontrar y corregir los problemas adicionales.  
  
   A continuación, agregará código a la biblioteca de clases que se usará para mostrar las infracciones de la CA1704 "Los identificadores deberían tener la ortografía correcta" regla de análisis de código. Para obtener más información, consulte [CA1704: los identificadores deben estar escritos correctamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
#### <a name="add-your-own-code"></a>Agregar su propio código  
  
- En el Explorador de soluciones, abra el archivo Class1.cs y reemplace el código existente con lo siguiente:  
  
  ```  
  using System;  
  using System.Collections.Generic;  
  using System.Text;  
  
  namespace RuleSetSample  
  {  
      public class Class1  
      {  
          //The variable parameter names "a" and "b" will cause  
          //the warning CA 1704 Microsoft.Naming "Consider   
          //providing a more meaningful name" to fire  
          public int AddIntegers(int a, int b)  
          {  
  
              int sum = a + b;  
  
              return (sum);  
          }  
      }  
  }  
  
  ```  
  
  Ahora puede ejecutar análisis de código en el proyecto RuleSetSample y busque los errores y advertencias generadas en la ventana Lista de errores.  
  
#### <a name="run-code-analysis-on-the-rulesetsample-project"></a>Ejecutar análisis de código en el proyecto RuleSetSample  
  
1. En el **analizar** menú, haga clic en **ejecutar análisis de código en RuleSetSample**.  
  
2. En la ventana Lista de errores, haga clic en **advertencias** y, a continuación, haga clic en el **descripción** encabezado de columna para ordenar las advertencias en orden alfanumérico.  
  
    En una aplicación real, podría corregir cualquier infracción de regla que vale la pena corregir en este momento, o si lo desea desactivar o suprimir una regla si determinó que no era merece la pena corregir. Para obtener más información, consulte [suprimir las advertencias por uso de atributo SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).  
  
3. Tenga en cuenta las advertencias CA1704. Las infracciones de esta regla indican que debe "considerar proporcionar un nombre más significativo para los parámetros." Puede corregir el problema en el código o puede deshabilitar la regla, como se explica en el procedimiento siguiente.  
  
   A continuación, va a personalizar el conjunto de reglas para excluir la advertencia CA1704, "Los identificadores deberían tener la ortografía correcta".  
  
#### <a name="customize-the-rule-set-for-your-project-to-disable-a-specific-rule"></a>Personalizar el conjunto de reglas para que el proyecto deshabilitar una regla específica  
  
1. En el **analizar** menú, haga clic en **configurar análisis de código para RuleSetSample**.  
  
2. En el **ejecutar este conjunto de reglas** desplegable lista, compruebe que la **todas las reglas de Microsoft** todavía está resaltado el conjunto de reglas y, a continuación, haga clic en **abierto**. Se abrirá la página de conjunto de reglas.  
  
3. Expanda el nodo de categoría Microsoft.Naming y, a continuación, seleccione la advertencia CA1704.  
  
4. En el **acción** columna, seleccione **ninguno.** Esto evita que CA1704 mostrar como una advertencia o error en la ventana Lista de errores.  
  
    Ahora sería un buen momento para experimentar con los distintos botones de barra de herramientas y opciones de filtrado para familiarizarse con ellos. Por ejemplo, puede usar el **Group By** lista desplegable para buscar una regla específica o categoría de reglas. Otro ejemplo es que puede usar el **ocultar reglas deshabilitadas** botón en la barra de herramientas de páginas de conjunto de reglas para ocultar o mostrar todas las reglas con el **acción** columna establecida en **ninguno**. Esto puede ser útil si desea buscar todas las reglas que se ha desactivado para comprobar que aún desea que estén deshabilitados.  
  
5. En el menú Ver, haga clic en la ventana Propiedades. Tipo **My Custom Rule Set** en el cuadro Nombre de la ventana de herramientas de propiedades. Esto cambia el nombre para mostrar de la nueva regla se establece el [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] IDE.  
  
6. En el **archivo** menú, haga clic en **Rules.ruleset todos los Microsoft guardar** guardar la regla personalizada establecido. Vaya a la carpeta raíz del proyecto. En **el nombre de archivo** cuadro de texto, escriba **MyCustomRuleSet**. Ahora se puede seleccionar el conjunto de reglas personalizado para su uso con el proyecto.  
  
   Con el nuevo conjunto de reglas creado, ahora tiene que configurar la configuración del proyecto para especificar que desea usar la nueva regla establecido con él.  
  
#### <a name="specify-the-new-rule-set-for-use-with-your-project"></a>Especifique la nueva regla de configuración para usarlo con el proyecto  
  
1. En el Explorador de soluciones, haga clic en el proyecto y, a continuación, seleccione **propiedades**.  
  
2. En el **propiedades** , haga clic **análisis de código**.  
  
    En el **ejecutar este conjunto de reglas** la lista desplegable, haga clic en  **\<Examinar... >**. Vaya a la carpeta raíz del proyecto de código y, a continuación, seleccione **MyCustomRuleSet.ruleset**. Este es el nuevo conjunto de reglas que ha creado en el procedimiento anterior.  
  
3. En el **archivo** menú, haga clic en **guardar** para guardar la configuración del proyecto. Ahora se puede usar el conjunto de reglas personalizado con el proyecto.  
  
   Por último, se ejecutará el análisis de código nuevo con su conjunto de reglas MyCustomRuleSet. Tenga en cuenta que la ventana Lista de errores no se muestra la infracción de regla de rendimiento CA1704.  
  
#### <a name="run-code-analysis-on-the-rulesetsample-project-for-the-second-time"></a>Ejecutar análisis de código en el proyecto RuleSetSample por segunda vez  
  
1.  En el **analizar** menú, haga clic en **ejecutar análisis de código en RuleSetSample**.  
  
2.  En la ventana Lista de errores, tenga en cuenta que al hacer clic en **advertencias**, ya no verá las infracciones de la advertencia CA1704 para la regla "Los identificadores deberían tener la ortografía correcta".  
  
## <a name="see-also"></a>Vea también  
 [Cómo: configurar el análisis de código para un proyecto de código administrado](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)   
 [Referencia del conjunto de reglas Análisis de código](../code-quality/code-analysis-rule-set-reference.md)



