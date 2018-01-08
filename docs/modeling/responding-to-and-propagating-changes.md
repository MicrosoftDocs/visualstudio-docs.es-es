---
title: Responder a y propagar los cambios | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, events
ms.assetid: fc2e9ac5-7a84-44ed-9945-94e45f89c227
caps.latest.revision: "24"
author: alancameronwills
ms.author: awills
manager: douge
ms.workload: multiple
ms.openlocfilehash: cebfaa79e2524dcd6ba862ec55467acc9e5cd316
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="responding-to-and-propagating-changes"></a>Responder a los cambios y propagarlos
Cuando un elemento se crea, elimina o actualiza, puede escribir código que se propaga el cambio a otras partes del modelo o a recursos externos como archivos, bases de datos u otros componentes.  
  
## <a name="in-this-section"></a>En esta sección  
 Como norma, tenga en cuenta estas técnicas en el siguiente orden:  
  
|Técnica|Escenarios|Para obtener más información|  
|---------------|---------------|--------------------------|  
|Defina una propiedad de dominio calculado.|Una propiedad de dominio cuyo valor se calcula a partir de otras propiedades en el modelo. Por ejemplo, un precio que es la suma de precios de elementos relacionados.|[Propiedades calculadas y de almacenamiento personalizado](../modeling/calculated-and-custom-storage-properties.md)|  
|Defina una propiedad de dominio de almacenamiento personalizado.|Una propiedad de dominio que se almacenan en otras partes del modelo o externamente. Por ejemplo, podría analizar una cadena de expresión en un árbol en el modelo.|[Propiedades calculadas y de almacenamiento personalizado](../modeling/calculated-and-custom-storage-properties.md)|  
|Invalidar los controladores de cambio como OnValueChanging y OnDeleting|Mantener los distintos elementos sincronizados y mantenerlos sincronizados con el modelo de valores externos.<br /><br /> Restringir los valores a intervalos definidos.<br /><br /> Se llama inmediatamente antes y después el valor de propiedad y otros cambios. Puede finalizar el cambio iniciando una excepción.|[Controladores de los cambios de valor de propiedad de dominio](../modeling/domain-property-value-change-handlers.md)|  
|Reglas|Puede definir reglas que se ponen en cola para su ejecución justo antes del final de una transacción en el que se ha producido un cambio. No se ejecutan en Deshacer o rehacer. Usan para mantener sincronizados en sí una parte de la tienda.|[Las reglas propagan los cambios dentro del modelo](../modeling/rules-propagate-changes-within-the-model.md)|  
|Eventos de almacén|El almacén de modelado proporciona notificaciones de eventos, como agregar o eliminar un elemento o vínculo o cambiar el valor de una propiedad. El evento también se ejecuta en Deshacer y rehacer. Usar eventos de almacén para actualizar los valores que no están en el almacén.|[Los controladores de eventos propagan cambios fuera del modelo](../modeling/event-handlers-propagate-changes-outside-the-model.md)|  
|Eventos de .NET|Las formas tienen controladores de eventos que responden a los clics del mouse y otros movimientos. Tiene que registrar estos eventos para cada objeto. Registro normalmente se realiza en un reemplazo del InitializeInstanceResources y debe realizarse para cada elemento.<br /><br /> Normalmente, estos eventos se producen fuera de una transacción.|[Cómo: Interceptar un clic en una forma o decorador](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)|  
|Reglas de límites|Una regla de límites se utiliza específicamente para restringir los límites de una forma.|[Ubicación y tamaño de las reglas de restricción de formas BoundsRules](../modeling/boundsrules-constrain-shape-location-and-size.md)|  
|Reglas de selección|Las reglas de selección específicamente restringen lo que el usuario puede seleccionar.|[Cómo: Tener acceso a una selección y restringir la selección actual](../modeling/how-to-access-and-constrain-the-current-selection.md)|  
|OnAssocatedPropertyChanged|Indicar los Estados de los elementos del modelo con las características de formas y conectores como instantáneas, puntas de flecha, color y ancho de línea y el estilo.|[Actualizar formas y conectores para reflejar el modelo](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)|  
  
## <a name="comparing-rules-and-store-events"></a>**Comparar las reglas y los eventos de almacén**  
 Cambio notificadores, reglas y los eventos se ejecutan cuando se producen cambios en un modelo.  
  
 Normalmente se aplican las reglas en el final de la transacción en la que se ha producido el cambio y eventos se aplican después de confirmadas los cambios en una transacción.  
  
 Usar eventos de almacén para sincronizar el modelo con objetos fuera del almacén y las reglas para mantener la coherencia en el almacén.  
  
-   **Crear reglas personalizadas** crear una regla personalizada como una clase derivada de una regla abstracta. También debe notificar el marco de trabajo acerca de la regla personalizada. Para obtener más información, consulte [propagar los cambios en el modelo de reglas de](../modeling/rules-propagate-changes-within-the-model.md).  
  
-   **Suscribirse a eventos** para poder suscribirse a un evento, cree un controlador de eventos y el delegado. A continuación, utilice el <xref:Microsoft.VisualStudio.Modeling.Store.EventManagerDirectory%2A>propiedad que se va a suscribirse al evento. Para obtener más información, consulte [controladores propagar cambios fuera el modelo de evento](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
-   **Deshacer cambios** al deshacer una transacción, se generan eventos, pero no se aplican las reglas. Si una regla cambia un valor y deshacer este cambio, el valor se restablece al valor original durante la acción de deshacer. Cuando se genera un evento, debe cambiar manualmente el valor a su valor original. Para obtener más información sobre transactons y deshacer, consulte [Cómo: usar transacciones para actualizar el modelo](../modeling/how-to-use-transactions-to-update-the-model.md).  
  
-   **Pasar argumentos de evento a los eventos y las reglas de** ambos eventos y se pasan las reglas de un `EventArgs` cambia de parámetro que tiene información sobre cómo el modelo.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: interceptar al hacer clic en una forma o un elemento Decorator](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)   
 [Escribir código para personalizar lenguajes específicos de dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)