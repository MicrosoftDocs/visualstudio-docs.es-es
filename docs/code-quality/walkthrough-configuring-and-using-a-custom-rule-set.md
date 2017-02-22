---
title: "Tutorial: Configurar y utilizar un conjunto de reglas personalizado | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "análisis de código, tutoriales"
  - "análisis de código, conjuntos de reglas"
ms.assetid: 7fe0a4e3-1ce0-4f38-a87a-7d81238ec7cd
caps.latest.revision: 40
caps.handback.revision: 40
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tutorial: Configurar y utilizar un conjunto de reglas personalizado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En este tutorial se muestra cómo emplear las herramientas de análisis del código que se han configurado para usar un *conjunto de reglas* personalizado en una biblioteca de clases.  Puede seleccionar un conjunto de reglas relacionadas con el tipo de proyecto que especificó para la solución o puede seleccionar otros conjuntos de reglas para satisfacer una necesidad concreta, por ejemplo, examinar el código heredado para buscar problemas que se pueden corregir sin necesidad de interrupción.  En ambos casos puede personalizar los conjuntos de reglas de manera que se ajusten a los requisitos de un proyecto.  
  
 En este tutorial, llevará a cabo estos procesos:  
  
-   Crear una biblioteca de clases.  
  
-   Seleccionar el conjunto de reglas de análisis de código **Reglas de directrices de diseño básicas de Microsoft**.  
  
-   Agregar su código propio a la clase.  
  
-   Ejecutar análisis de código.  
  
-   Personalizar el conjunto de reglas.  
  
-   Ejecutar análisis de código y ver cómo funciona el comportamiento de la personalización del conjunto de reglas.  
  
## Requisitos previos  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] o [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
## Utilizar conjuntos de reglas con análisis de código  
 Primero, cree una biblioteca de clases simple.  
  
#### Crear una biblioteca de clases  
  
1.  En el menú **Archivo**, haga clic en **Nuevo** y, a continuación, haga clic en **Proyecto**.  
  
2.  En el cuadro de diálogo **Nuevo proyecto**, en **Tipos de proyecto**, haga clic en **Visual C\#**.  
  
3.  En **Visual C\#**, seleccione **Biblioteca de clases**.  
  
4.  En el cuadro de texto **Nombre**, escriba **RuleSetSample** y, a continuación, haga clic en Aceptar.  
  
 A continuación, seleccionará el conjunto de reglas **Reglas de directrices de diseño básicas de Microsoft** y lo guardará con su proyecto.  
  
#### Seleccionar un conjunto de reglas de análisis de código  
  
1.  En el menú **Analizar**, haga clic en **Configurar análisis de código para RuleSetSample**.  
  
     Aparece la configuración del análisis de código.  
  
2.  En la lista desplegable **Ejecutar este conjunto de reglas**, seleccione **Todas las reglas de Microsoft**.  
  
     Para obtener más información acerca de los conjuntos de reglas disponibles, vea [Referencia del conjunto de reglas Análisis de código](../code-quality/code-analysis-rule-set-reference.md).  
  
     En el menú Archivo, haga clic en **Guardar los elementos seleccionados** para actualizar el archivo de proyecto con información sobre el conjunto de reglas seleccionado y sus valores.  
  
    > [!TIP]
    >  En una situación real, una práctica recomendada para clasificar por orden de prioridad los problemas que se desean abordar con el análisis de código es comenzar con el conjunto de **Reglas mínimas recomendadas de Microsoft** y corregir los problemas y, después, agregar incrementalmente más reglas o conjuntos de reglas para buscar y corregir otros problemas.  
  
 A continuación, agregará código a la biblioteca de clases que se utilizará para mostrar las infracciones de la regla de análisis de código CA1704 "Los identificadores deberían tener la ortografía correcta".  Para obtener más información, vea [CA1704: Los identificadores deberían tener la ortografía correcta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
#### Agregar su propio código  
  
-   En el Explorador de soluciones, abra el archivo Class1.cs y reemplace el código existente por el siguiente:  
  
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
  
 Ahora puede ejecutar el análisis de código en el proyecto RuleSetSample y buscar errores y advertencias generadas en la ventana Lista de errores.  
  
#### Ejecutar el análisis de código en el proyecto RuleSetSample  
  
1.  En el menú **Analizar**, haga clic en **Ejecutar análisis de código en RuleSetSample**.  
  
2.  En la ventana Lista de errores, haga clic en **Advertencias** y, a continuación, haga clic en el encabezado de columna **Descripción** para ordenar las advertencias alfanuméricamente.  
  
     En una aplicación real, corregiría cualquier infracción de regla que mereciera la pena corregir en este punto u opcionalmente desactivaría o suprimiría una regla si decide que no vale la pena corregirla.  Para obtener más información, vea [Suprimir advertencias mediante el atributo SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).  
  
3.  Observe las advertencias CA1704.  Las infracciones de esta regla indican que debe "considerar proporcionar un nombre más descriptivo para los parámetros". Podría corregir el problema en el código o deshabilitar la regla, tal y como se explica en el procedimiento siguiente.  
  
 Después, personalizará el conjunto de reglas para que excluya la advertencia CA1704, "Los identificadores deberían tener la ortografía correcta".  
  
#### Personalizar el conjunto de reglas en su proyecto para deshabilitar una regla concreta  
  
1.  En el menú **Analizar**, haga clic en **Configurar análisis de código para RuleSetSample**.  
  
2.  En la lista desplegable **Ejecutar este conjunto de reglas**, compruebe que todavía está resaltado **Todas las reglas de Microsoft** y, a continuación, haga clic en **Abrir**.  Se muestra la página del conjunto de reglas.  
  
3.  Expanda el nodo de la categoría Microsoft.Naming y, a continuación, seleccione la advertencia CA1704.  
  
4.  En la columna **Acción**, seleccione **Ninguna**. Esto evita que CA1704 se muestre como una advertencia o error en la ventana Lista de errores.  
  
     Este es un buen momento para experimentar con los distintos botones de la barra de herramientas y las opciones de filtrado para familiarizarse con ellos.  Por ejemplo, puede utilizar la lista desplegable  **Agrupar por** para buscar una regla o categoría de reglas concreta.  Otro ejemplo es que puede utilizar el botón **Ocultar reglas deshabilitadas** de la barra de herramientas de páginas del conjunto de reglas para ocultar o mostrar todas las reglas que tienen la columna **Acción** establecida en **Ninguna**.  Esto puede ser útil si desea buscar reglas que haya desactivado para comprobar que siguen deshabilitadas.  
  
5.  En el menú Ver, haga clic en la Ventana Propiedades.  Escriba **My Custom Rule Set** en el cuadro Nombre de la ventana de herramientas de Propiedades.  De esta manera se cambia el nombre para mostrar del nuevo conjunto de reglas en el IDE de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  
  
6.  En el menú **Archivo**, haga clic en **Guardar todas las reglas de Microsoft.ruleset** para guardar su conjunto de reglas personalizado.  Navegar hasta la carpeta raíz del proyecto.  En el cuadro **Nombre de archivo**, escriba MyCustomRuleSet.  El conjunto de reglas personalizado puede ahora seleccionarse para el uso con el proyecto.  
  
 Con el nuevo conjunto de reglas creado, tiene que configurar los valores del proyecto para especificar que desea utilizar el nuevo conjunto de reglas.  
  
#### Especificar el nuevo conjunto de reglas para usar con el proyecto  
  
1.  En el Explorador de soluciones, haga clic con el botón secundario del mouse en el proyecto y, a continuación, seleccione **Propiedades**.  
  
2.  En la pestaña **Propiedades**, haga clic en **Análisis de código**.  
  
     En la lista desplegable de **Ejecutar este conjunto de reglas** , haga clic en **\<Examinar\>**.  Navegue hasta la carpeta raíz del proyecto de código y seleccione MyCustomRuleSet.ruleset.  Este es el nuevo conjunto de reglas que creó en el procedimiento anterior.  
  
3.  En el menú **Archivo**, haga clic en **Guardar** para guardar la configuración del proyecto.  El conjunto de reglas personalizado ya se puede utilizar con el proyecto.  
  
 Finalmente, ejecutará el análisis de código de nuevo usando su conjunto de reglas MyCustomRuleSet.  Observe que la ventana Lista de errores no muestra la infracción de la regla de rendimiento CA1704.  
  
#### Ejecutar el análisis de código en el proyecto RuleSetSample por segunda vez  
  
1.  En el menú **Analizar**, haga clic en **Ejecutar análisis de código en RuleSetSample**.  
  
2.  En la ventana Lista de errores, observe que al hacer clic en **Advertencias**, ya no aparecen las infracciones del advertencia CA1704 de la regla "Los identificadores deberían tener la ortografía correcta".  
  
## Vea también  
 [Cómo: Configurar el análisis de código para un proyecto de código administrado](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)   
 [Referencia del conjunto de reglas Análisis de código](../code-quality/code-analysis-rule-set-reference.md)