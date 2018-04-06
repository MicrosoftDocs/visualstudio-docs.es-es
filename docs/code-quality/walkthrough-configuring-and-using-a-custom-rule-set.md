---
title: 'Tutorial: Configurar y utilizar un personalizado conjunto de reglas | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-code-analysis
ms.topic: article
helpviewer_keywords:
- code analysis, walkthroughs
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b72a86f10c6e864406929fdccfb59bdd9393752e
ms.sourcegitcommit: a0a49cceb0fdc1465ddf76d131c6575018b628b8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2018
---
# <a name="walkthrough-configuring-and-using-a-custom-rule-set"></a>Tutorial: Configurar y utilizar un conjunto de reglas personalizado

Este tutorial muestra cómo utilizar las herramientas de análisis de código que se ha configurado para usar un personalizada *conjunto de reglas* en una biblioteca de clases. Puede seleccionar un conjunto de reglas que se relaciona con el tipo de proyecto que especificó para la solución, o puede seleccionar otros conjuntos de reglas para satisfacer una necesidad concreta como el análisis de código heredado para problemas que puede corregirse de una manera sin interrupción. En cualquier caso, los conjuntos de reglas también pueden personalizarse para ajustar a los requisitos del proyecto.  
  
En este tutorial, recorre paso a paso a través de estos procesos:  
  
-   Crear una biblioteca de clases.  
  
-   Seleccione el **reglas de directrices de diseño básicas de Microsoft** conjunto de reglas de análisis de código.  
  
-   Agregue su propio código a la clase.  
  
-   Ejecutar análisis de código.  
  
-   Personalizar el conjunto de reglas.  
  
-   Ejecutar análisis de código y ver cómo el conjunto de reglas personalización funciona el comportamiento.  
  
## <a name="using-rule-sets-with-code-analysis"></a>Utilizar conjuntos de reglas con análisis de código

En primer lugar, cree una biblioteca de clases simple.  
  
### <a name="create-a-class-library"></a>Crear una biblioteca de clases  
  
1.  En el menú **Archivo** , haga clic en **Nuevo** y, a continuación, haga clic en **Proyecto**.  
  
2.  En el **nuevo proyecto** cuadro de diálogo **tipos de proyecto**, haga clic en **Visual C#**.  
  
3.  En **Visual C#**, seleccione **biblioteca de clases**.  
  
4.  En el **nombre** cuadro de texto, escriba **RuleSetSample** y, a continuación, haga clic en **Aceptar**.  
  
 A continuación, seleccionará el **reglas de directrices de diseño básicas de Microsoft** conjunto de reglas y guárdelo con el proyecto.  
  
### <a name="select-a-code-analysis-rule-set"></a>Seleccione un conjunto de reglas de análisis de código  
  
1.  En el **analizar** menú, haga clic en **configurar análisis de código para RuleSetSample**.  
  
     Aparecen los valores de configuración para el análisis de código.  
  
2.  En el **ejecutar este conjunto de reglas** lista desplegable, seleccione **todas las reglas de Microsoft**.  
  
     Para obtener más información acerca de los conjuntos de reglas disponibles, vea [referencia de conjunto de reglas de análisis de código](../code-quality/code-analysis-rule-set-reference.md).  
  
     En el menú archivo, haga clic en **guardar elementos seleccionados** para actualizar el archivo de proyecto con información sobre el conjunto de reglas que ha seleccionado y su configuración.  
  
    > [!TIP]
    >  En una situación real, una buena práctica de usar para asignar prioridades a los problemas de destino con el análisis de código es comenzar con la **reglas mínimas recomendadas** conjunto de reglas y corregir los problemas deseados y, a continuación, agregar de forma incremental más reglas o la regla se establece para buscar y corregir los problemas adicionales.  
  
 A continuación, agregará código a la biblioteca de clases que se usará para mostrar las infracciones de la CA1704 "Los identificadores deberían tener la ortografía correcta" regla de análisis de código. Para obtener más información, consulte [CA1704: los identificadores deberían tener la ortografía correcta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
### <a name="add-your-own-code"></a>Agregar su propio código  
  
-   En el Explorador de soluciones, abra el archivo Class1.cs y reemplace el código existente con lo siguiente:  
  
    ```csharp
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
  
Ahora puede ejecutar análisis de código en el proyecto RuleSetSample y buscar errores y advertencias generadas en la ventana Lista de errores.  
  
### <a name="run-code-analysis-on-the-rulesetsample-project"></a>Ejecutar análisis de código en el proyecto RuleSetSample  
  
1.  En el **analizar** menú, haga clic en **ejecutar análisis de código en RuleSetSample**.  
  
2.  En la ventana Lista de errores, haga clic en **advertencias** y, a continuación, haga clic en el **descripción** encabezado de columna para ordenar las advertencias por orden alfanumérico.  
  
     En una aplicación del mundo real, se podría corregir cualquier infracción de regla merece la pena corregir en este punto, o si lo desea desactivar o suprimir una regla si ha determinado que no se implementó la pena corregir. Para obtener más información, consulte [Suprimir advertencias](../code-quality/in-source-suppression-overview.md).
  
3.  Tenga en cuenta las advertencias CA1704. Las infracciones de esta regla indican que debe "considerar proporcionar un nombre más descriptivo para los parámetros." Puede corregir el problema en el código o se puede deshabilitar la regla, tal como se describe en el procedimiento siguiente.  
  
 A continuación, personalizará el conjunto de reglas para excluir la advertencia CA1704, "Los identificadores deberían tener la ortografía correcta".  
  
### <a name="customize-the-rule-set-for-your-project-to-disable-a-specific-rule"></a>Personalizar el conjunto de reglas para que su proyecto para deshabilitar una regla específica  
  
1.  En el **analizar** menú, haga clic en **configurar análisis de código para RuleSetSample**.  
  
2.  En el **ejecutar este conjunto de reglas** lista desplegable lista, compruebe que la **todas las reglas de Microsoft** todavía se resalta el conjunto de reglas y, a continuación, haga clic en **abiertos**. Se abrirá la página de conjunto de reglas.  
  
3.  Expanda el nodo de categoría Microsoft.Naming y, a continuación, seleccione la advertencia CA1704.  
  
4.  En el **acción** columna, seleccione **ninguno.** Esto evita que CA1704 mostrar como una advertencia o un error en la ventana Lista de errores.  
  
     Ahora es un buen momento para experimentar con los distintos botones de barra de herramientas y opciones de filtrado para familiarizarse con ellos. Por ejemplo, puede usar el **Group By** la lista desplegable para ayudar a localizar una regla específica, o categoría de reglas. Otro ejemplo es que puede usar el **ocultar reglas deshabilitadas** botón en la barra de herramientas de páginas de conjunto de reglas para ocultar o mostrar todas las reglas con el **acción** columna establecida en **ninguno**. Esto puede ser útil si desea buscar todas las reglas que ha desactivado para comprobar que aún desea tenerlas deshabilitado.  
  
5.  En el menú Ver, haga clic en ventana Propiedades. Tipo de **My Custom Rule Set** en el cuadro Nombre de la ventana de herramientas de propiedades. Esto cambia el nombre para mostrar de la nueva regla establecido el [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] IDE.  
  
6.  En el **archivo** menú, haga clic en **Rules.ruleset todos los Microsoft guardar** guardar la regla personalizada establecido. Navegue a la carpeta raíz del proyecto. En **el nombre de archivo** cuadro de texto, escriba **MyCustomRuleSet**. El conjunto de reglas personalizado puede ahora seleccionarse para su uso con el proyecto.  
  
Con el nuevo conjunto de reglas creado, ahora tendrá que configurar la configuración del proyecto para especificar que desea usar la nueva regla establecer con él.  
  
### <a name="specify-the-new-rule-set-for-use-with-your-project"></a>Especifique la nueva regla establecer para su uso con el proyecto  
  
1.  En el Explorador de soluciones, haga clic en el proyecto y, a continuación, seleccione **propiedades**.  
  
2.  En el **propiedades** , haga clic en **análisis de código**.  
  
     En el **ejecutar este conjunto de reglas** la lista desplegable, haga clic en  **\<Examinar... >**. Navegue hasta la carpeta raíz de su proyecto de código y, a continuación, seleccione **MyCustomRuleSet.ruleset**. Este es el nuevo conjunto de reglas que creó en el procedimiento anterior.  
  
3.  En el **archivo** menú, haga clic en **guardar** para guardar la configuración del proyecto. Ahora se puede utilizar el conjunto de reglas personalizado con el proyecto.  
  
 Por último, ejecutará el análisis de código con el conjunto de reglas MyCustomRuleSet. Tenga en cuenta que la ventana Lista de errores no se muestra la infracción de regla de rendimiento CA1704.  
  
### <a name="run-code-analysis-on-the-rulesetsample-project-for-the-second-time"></a>Ejecutar análisis de código en el proyecto RuleSetSample por segunda vez  
  
1.  En el **analizar** menú, haga clic en **ejecutar análisis de código en RuleSetSample**.  
  
2.  En la ventana Lista de errores, tenga en cuenta que al hacer clic en **advertencias**, ya no verá las infracciones de la advertencia CA1704 de la regla "Los identificadores deberían tener la ortografía correcta".  
  
## <a name="see-also"></a>Vea también

[Cómo: configurar el análisis de código para un proyecto de código administrado](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)   
[Referencia del conjunto de reglas Análisis de código](../code-quality/code-analysis-rule-set-reference.md)