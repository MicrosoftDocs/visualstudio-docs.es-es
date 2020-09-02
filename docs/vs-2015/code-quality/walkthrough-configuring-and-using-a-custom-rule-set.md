---
title: 'Tutorial: configurar y usar un conjunto de reglas personalizado | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, walkthroughs
- code analysis, rule sets
ms.assetid: 7fe0a4e3-1ce0-4f38-a87a-7d81238ec7cd
caps.latest.revision: 42
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8239afd1cf4e8c0a5e702f2b0e4ed64408cada09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645741"
---
# <a name="walkthrough-configuring-and-using-a-custom-rule-set"></a>Tutorial: Configurar y utilizar un conjunto de reglas personalizado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tutorial se muestra cómo usar las herramientas de análisis de código que se han configurado para usar un *conjunto de reglas* personalizado en una biblioteca de clases. Puede seleccionar un conjunto de reglas relacionado con el tipo de proyecto que especificó para la solución, o puede seleccionar conjuntos de reglas alternativos para satisfacer una necesidad específica, como examinar el código heredado en busca de problemas que se puedan corregir de forma no interrumpida. En cualquier caso, los conjuntos de reglas también se pueden personalizar para ajustarlos a los requisitos del proyecto.

 En este tutorial, recorrerá paso a paso estos procesos:

- Cree una biblioteca de clases.

- Seleccione el conjunto de reglas de análisis de código **reglas de directrices de diseño básicas de Microsoft** .

- Agregue su propio código a la clase.

- Ejecutar análisis de código.

- Personalizar el conjunto de reglas.

- Ejecute el análisis de código y vea cómo funciona el comportamiento de personalización del conjunto de reglas.

## <a name="prerequisites"></a>Prerrequisitos

- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]o [!INCLUDE[vsPro](../includes/vspro-md.md)]

## <a name="using-rule-sets-with-code-analysis"></a>Usar conjuntos de reglas con el análisis de código
 En primer lugar, cree una biblioteca de clases simple.

#### <a name="create-a-class-library"></a>Creación de una biblioteca de clases

1. En el menú **Archivo**, haga clic en **Nuevo** y, a continuación, haga clic en **Proyecto**.

2. En el cuadro de diálogo **nuevo proyecto** , en **tipos de proyecto**, haga clic en **Visual C#**.

3. En **Visual C#**, seleccione **biblioteca de clases**.

4. En el cuadro de texto **nombre** , escriba **RuleSetSample** y, a continuación, haga clic en **Aceptar**.

   A continuación, seleccionará el conjunto de reglas **reglas de directrices de diseño básicas de Microsoft** y lo guardará en el proyecto.

#### <a name="select-a-code-analysis-rule-set"></a>Seleccionar un conjunto de reglas de análisis de código

1. En el menú **analizar** , haga clic en **configurar análisis de código para RuleSetSample**.

    Aparecen los valores de configuración para el análisis de código.

2. En la lista desplegable **ejecutar este conjunto de reglas** , seleccione **Microsoft All Rules (todas las reglas**).

    Para obtener más información sobre los conjuntos de reglas disponibles, vea [Referencia del conjunto de reglas de análisis de código](../code-quality/code-analysis-rule-set-reference.md).

    En el menú Archivo, haga clic en **guardar los elementos seleccionados** para actualizar el archivo de proyecto con información sobre el conjunto de reglas seleccionado y su configuración.

   > [!TIP]
   > En una situación real, una buena práctica para dar prioridad a los problemas que desea destinar al análisis de código es comenzar con el conjunto de reglas de **reglas mínimas recomendadas** y corregir los problemas deseados y, a continuación, agregar incrementalmente más reglas o conjuntos de reglas para buscar y corregir los problemas adicionales.

   A continuación, agregará código a la biblioteca de clases, que se usará para mostrar las infracciones de la regla de análisis de código "los identificadores deberían estar escritos correctamente". Para obtener más información, vea [CA1704: los identificadores deberían estar escritos correctamente](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

#### <a name="add-your-own-code"></a>Agregar su propio código

- En Explorador de soluciones, abra el archivo Class1.cs y reemplace el código existente por lo siguiente:

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

  Ahora puede ejecutar el análisis de código en el proyecto RuleSetSample y buscar los errores y advertencias generados en la ventana Lista de errores.

#### <a name="run-code-analysis-on-the-rulesetsample-project"></a>Ejecutar análisis de código en el proyecto RuleSetSample

1. En el menú **analizar** , haga clic en **Ejecutar Análisis de código en RuleSetSample**.

2. En la ventana Lista de errores, haga clic en **advertencias** y, a continuación, haga clic en el encabezado de columna **Descripción** para ordenar las advertencias alfanuméricamente.

    En una aplicación real, corregiría cualquier infracción de regla que merece la pena corregir en este punto, o bien desactivar o suprimir opcionalmente una regla si determinó que no merece la pena corregir. Para más información, vea [Suprimir advertencias mediante el atributo SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).

3. Tenga en cuenta las advertencias de CA1704. Estas infracciones en esta regla indican que debe "considerar proporcionar un nombre más significativo para los parámetros". Puede corregir el problema en el código o puede deshabilitar la regla, tal como se explica en el procedimiento siguiente.

   A continuación, personalizará el conjunto de reglas para excluir la advertencia CA1704 "los identificadores deben estar escritos correctamente".

#### <a name="customize-the-rule-set-for-your-project-to-disable-a-specific-rule"></a>Personalizar el conjunto de reglas para que el proyecto deshabilite una regla específica

1. En el menú **analizar** , haga clic en **configurar análisis de código para RuleSetSample**.

2. En la lista desplegable **ejecutar este conjunto de reglas** , compruebe que el conjunto de reglas **todas las reglas de Microsoft** sigue estando resaltado y, a continuación, haga clic en **abrir**. Se muestra la página conjunto de reglas.

3. Expanda el nodo Microsoft. naming Category y, a continuación, seleccione la advertencia CA1704.

4. En la columna **acción** , seleccione **ninguno.** Esto impide que CA1704 se muestre como una advertencia o un error en la ventana Lista de errores.

    Ahora sería un buen momento para experimentar con los distintos botones de la barra de herramientas y las opciones de filtrado para familiarizarse con ellos. Por ejemplo, puede usar la lista desplegable **Agrupar por** para buscar una regla específica o una categoría de reglas. Otro ejemplo es que puede usar el botón **Ocultar reglas deshabilitadas** en la barra de herramientas de las páginas del conjunto de reglas para ocultar o mostrar todas las reglas con la columna **acción** establecida en **ninguno**. Esto puede ser útil si desea buscar las reglas que ha desactivado para comprobar que aún desea deshabilitarlas.

5. En el menú Ver, haga clic en Ventana de propiedades. Escriba **mi conjunto de reglas personalizado** en el cuadro Nombre de la ventana de herramientas de propiedades. Esto cambia el nombre para mostrar del nuevo conjunto de reglas en el [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] IDE.

6. En el menú **archivo** , haga clic en **Guardar Microsoft All rules. ruleset** para guardar el conjunto de reglas personalizado. Vaya a la carpeta raíz del proyecto. En **el** cuadro de texto nombre de archivo, escriba **MyCustomRuleSet**. Ahora se puede seleccionar el conjunto de reglas personalizado para su uso con el proyecto.

   Una vez creado el nuevo conjunto de reglas, tendrá que configurar el proyecto para especificar que desea usar el nuevo conjunto de reglas.

#### <a name="specify-the-new-rule-set-for-use-with-your-project"></a>Especificar el conjunto de reglas nuevo para su uso con el proyecto

1. En Explorador de soluciones, haga clic con el botón secundario en el proyecto y seleccione **propiedades**.

2. En la pestaña **propiedades** , haga clic en **análisis de código**.

    En la lista desplegable **ejecutar este conjunto de reglas** , haga clic en **\<Browse..>** . Vaya a la carpeta raíz del proyecto de código y, a continuación, seleccione **MyCustomRuleSet. ruleset**. Este es el nuevo conjunto de reglas creado en el procedimiento anterior.

3. En el menú **archivo** , haga clic en **Guardar** para guardar la configuración del proyecto. Ahora se puede usar el conjunto de reglas personalizado con el proyecto.

   Por último, volverá a ejecutar el análisis de código con el conjunto de reglas de MyCustomRuleSet. Tenga en cuenta que la ventana de Lista de errores no muestra la infracción de la regla de rendimiento CA1704.

#### <a name="run-code-analysis-on-the-rulesetsample-project-for-the-second-time"></a>Ejecutar análisis de código en el proyecto RuleSetSample por segunda vez

1. En el menú **analizar** , haga clic en **Ejecutar Análisis de código en RuleSetSample**.

2. En la ventana Lista de errores, tenga en cuenta que al hacer clic en **advertencias**, ya no verá las infracciones de advertencia de CA1704 para la regla "los identificadores deben estar escritos correctamente".

## <a name="see-also"></a>Consulte también
 [Cómo: configurar el análisis de código para un proyecto de código administrado referencia del conjunto de reglas de análisis de](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md) [código](../code-quality/code-analysis-rule-set-reference.md)
