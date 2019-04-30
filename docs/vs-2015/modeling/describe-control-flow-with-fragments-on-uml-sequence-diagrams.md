---
title: Describir el flujo de control con fragmentos de diagramas de secuencia UML | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.sequencediagram.combinedfragment.interactionoperand
- vs.teamarch.sequencediagram.combinedfragment
helpviewer_keywords:
- UML sequence diagrams, control flow
- UML sequence diagrams, fragments
- sequence diagrams, fragments
- sequence diagrams, control flow
ms.assetid: efcc0949-be7e-4cf4-99ef-47c36b3803ae
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c296be2e3a00efcdf48bdd6e4442e88fc32b3695
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63422534"
---
# <a name="describe-control-flow-with-fragments-on-uml-sequence-diagrams"></a>Describir el flujo de control con fragmentos de diagramas de secuencia de UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En un diagrama de secuencia UML, los *fragmentos combinados* permiten mostrar bucles, bifurcaciones y otras alternativas.  
  
 Un fragmento combinado se compone de uno o varios *operandos de interacción*, y cada uno de ellos incluye uno o varios mensajes, usos de interacción o fragmentos combinados.  
  
> [!NOTE]
> Este tema trata sobre los fragmentos en los diagramas de secuencia. Para obtener más información sobre cómo leer diagramas de secuencia UML, vea [diagramas de secuencia UML: referencia](../modeling/uml-sequence-diagrams-reference.md). Para obtener más información sobre cómo dibujar diagramas de secuencia UML, vea [diagramas de secuencia UML: Directrices](../modeling/uml-sequence-diagrams-guidelines.md).  
  
 ![El fragmento con dos operandos de interacción combinado](../modeling/media/uml-seqfragments.png "UML_SeqFragments")  
  
 Los elementos que aparecen en la ilustración son los siguientes.  
  
1. Un fragmento combinado. Hay varios tipos de fragmentos combinados. En este ejemplo es un fragmento combinado alternativo, que puede usar para mostrar que pueden producirse secuencias de mensajes alternativas.  
  
2. Operandos de interacción. Cada fragmento combinado contiene al menos un operando de interacción, que puede contener mensajes, usos de interacción y fragmentos combinados más pequeños. En este ejemplo, el fragmento combinado alternativo tiene dos operaciones de interacción, que muestran dos secuencias de mensajes alternativas.  
  
3. Puede seleccionar cada operando de interacción por separado haciendo dentro. En este ejemplo está seleccionado el operando de interacción superior, por lo que puede verse su límite. Normalmente, solo está visible la línea divisoria entre los operandos de interacción.  
  
    > [!NOTE]
    > Para seleccionar el operando de interacción superior, no debe pulsar demasiado cerca de la parte superior del fragmento combinado.  
  
4. Restricciones. Puede asignarle a cada operando de interacción una restricción. Esta describe la condición bajo la que se llevarán a cabo los mensajes incluidos en el operando de interacción.  
  
## <a name="creating-combined-fragments"></a>Crear fragmentos combinados  
 Para obtener una lista de los tipos de fragmento que puede crear, vea [Tipos de fragmentos combinados](#KindsOfFragment).  
  
#### <a name="to-create-a-combined-fragment"></a>Para crear un fragmento combinado  
  
1. Seleccione un mensaje o una secuencia de mensajes que comiencen en la misma línea de vida u ocurrencia de ejecución.  
  
   > [!NOTE]
   > Si selecciona varios mensajes, deben formar una secuencia ininterrumpida.  
  
2. Haga clic con el botón derecho en uno de los mensajes, seleccione **Rodear con**y haga clic en el tipo de fragmento combinado que desee, como **Fragmento combinado alternativo**.  
  
    Aparecerá un nuevo fragmento combinado. El encabezado indica el tipo de fragmento combinado seleccionado, como **Alt**.  
  
    Dentro del fragmento combinado, hay un fragmento que contiene los mensajes que seleccionó.  
  
   Puede agregar más operandos de interacción a algunos tipos de fragmentos combinados.  
  
   Después de reorganizar los mensajes dentro de un fragmento combinado, elija **Reorganizar diseño** en el menú contextual para cambiar el tamaño del fragmento combinado.  
  
#### <a name="to-add-a-new-interaction-operand-to-a-combined-fragment"></a>Para agregar un nuevo operando de interacción a un fragmento combinado  
  
1. Haga clic con el botón derecho en un espacio en blanco dentro del operando de interacción (2), fuera de cualquier fragmento que contenga, y debajo del encabezado del fragmento combinado.  
  
2. Seleccione **Agregar**.  
  
3. Haga clic en **Operando de interacción Before**o en **Operando de interacción After**.  
  
4. Puede agregar mensajes dentro del nuevo operando de interacción con las herramientas de mensajes, o bien copiando y pegando los mensajes existentes.  
  
   Puede establecer la propiedad **Guard** de un operando de interacción para describir las condiciones en que se realizan los mensajes que incluye. Por ejemplo, en un fragmento combinado **Loop** , puede usar la restricción para especificar la condición durante la cual el bucle continúa. En un fragmento combinado **Alt** , puede especificar una condición diferente para cada operando de interacción.  
  
#### <a name="to-set-the-guard-of-an-interaction-operand"></a>Para establecer la restricción de un operando de interacción  
  
1. Haga clic en un espacio en blanco dentro del operando de interacción (2), fuera de cualquier fragmento que contenga.  
  
    Aparece un borde de selección alrededor del operando de interacción y de la condición de restricción.  
  
    El encabezado de la ventana **Propiedades** muestra **Operando de interacción**.  
  
2. Escriba la condición de restricción.  
  
    La condición aparecerá cerca de la parte superior del fragmento (4).  
  
   Puede establecer las propiedades de algunos tipos de fragmentos combinados.  
  
#### <a name="to-set-or-view-the-properties-of-a-combined-fragment"></a>Para establecer o ver las propiedades de un fragmento combinado  
  
- Haga clic con el botón derecho en el título del fragmento combinado y, a continuación, haga clic en **Propiedades**.  
  
    > [!NOTE]
    > Los diferentes tipos de fragmentos combinados tienen propiedades diferentes.  
  
## <a name="KindsOfFragment"></a> Tipos de fragmentos combinados  
  
### <a name="fragments-describing-control-flow"></a>Fragmentos que describen el flujo de control  
 Un diagrama de secuencia sencillo muestra solo una secuencia típica. Puede usar los siguientes tipos de fragmentos combinados para describir las variaciones que pueden producirse en distintas ocasiones.  
  
|Tipo de fragmento|Descripción|  
|-------------------|-----------------|  
|**Opt**|Opcional. Contiene una secuencia que puede puede producirse o no. En la restricción, puede especificar la condición en la que se produce.|  
|**Alt**|Contiene una lista de fragmentos que incluyen secuencias de mensajes alternativas. Solo se produce una secuencia de cada vez.<br /><br /> Puede incluir una restricción en cada fragmento para indicar en qué circunstancias puede ejecutarse. Una restricción **else** indica un fragmento que debe ejecutarse si ninguna otra restricción es true. Si todas las restricciones son false y no hay ningún valor **else**, no se ejecuta ninguno de los fragmentos.|  
|**Loop**|El fragmento se repite cierto número de veces. En la restricción, puede indicar la condición en la que debe repetirse.<br /><br /> Los fragmentos combinados de bucle tienen las propiedades **Min** y **Max**, que indican el número mínimo y máximo de veces que el fragmento se puede repetir. El valor predeterminado es sin restricciones.|  
|**Break**|Si se ejecuta este fragmento, se abandona el resto de la secuencia. Puede usar la restricción para indicar la condición en la que se producirá la interrupción.|  
|**Par**|Parallel Los eventos de los fragmentos se pueden intercalar.|  
|**Crítico**|Se usa dentro de un fragmento Par o Seq. Indica que los mensajes de este fragmento no se deben intercalar con otros mensajes.|  
|**Seq**|Hay dos o más fragmentos de operando. Los mensajes relacionados con la misma línea de vida deben aparecer en el orden de los fragmentos. Si no implican las mismas líneas de vida, es posible intercalar en paralelo los mensajes de fragmentos diferentes.|  
|**Strict**|Hay dos o más fragmentos de operando. Los fragmentos deben aparecer en el orden indicado.|  
  
### <a name="fragments-about-how-to-interpret-the-sequence"></a>Fragmentos sobre cómo interpretar la secuencia  
 De forma predeterminada, el diagrama de secuencia indica una serie de mensajes que pueden aparecer. En el sistema que se está ejecutando, es posible que aparezcan otros mensajes que no eligiese para que se mostraran en el diagrama.  
  
 Los siguientes tipos de fragmentos pueden usarse para cambiar esta interpretación.  
  
|Tipo de fragmento|Descripción|  
|-------------------|-----------------|  
|**Considere la posibilidad de**|Especifica una lista de los mensajes que se describen en este fragmento. Pueden aparecer otros mensajes en el sistema que se está ejecutando, pero no son significativos para los propósitos de esta descripción.<br /><br /> Escriba la lista en la propiedad **Messages** .|  
|**Ignorar**|Lista de los mensajes que no se describen en este fragmento. Pueden aparecer en el sistema que se está ejecutando, pero no son significativos para los propósitos de esta descripción.<br /><br /> Escriba la lista en la propiedad **Messages** .|  
|**Assert**|El fragmento de operando especifica las únicas secuencias válidas. Suele usarse dentro de un fragmento Consider o Ignore.|  
|**Neg**|La secuencia que se muestra en este fragmento no debe producirse. Suele usarse dentro de un fragmento Consider o Ignore.|  
  
## <a name="see-also"></a>Vea también  
 [Diagramas de secuencia de UML: Directrices](../modeling/uml-sequence-diagrams-guidelines.md)   
 [Diagramas de secuencia de UML: Referencia](../modeling/uml-sequence-diagrams-reference.md)   
 [Editar modelos y diagramas UML](../modeling/edit-uml-models-and-diagrams.md)
