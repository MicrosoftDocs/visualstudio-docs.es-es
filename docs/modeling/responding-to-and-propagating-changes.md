---
title: Responder a los cambios y propagarlos
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 375f6996c91c294dd3b630c9ab987ff4b2d6cbdb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62824012"
---
# <a name="responding-to-and-propagating-changes"></a>Responder a los cambios y propagarlos
Cuando un elemento se crea, elimina o actualiza, puede escribir código que se propaga el cambio a otras partes del modelo o recursos externos, como archivos, bases de datos u otros componentes.

## <a name="in-this-section"></a>En esta sección
 Como norma, tenga en cuenta estas técnicas en el orden siguiente:

|Técnica|Escenarios|Para obtener más información|
|-|-|-|
|Definir una propiedad de dominio Calculated.|Una propiedad de dominio cuyo valor se calcula a partir de otras propiedades en el modelo. Por ejemplo, un precio que es la suma de los precios de los elementos relacionados.|[Propiedades calculadas y de almacenamiento personalizado](../modeling/calculated-and-custom-storage-properties.md)|
|Definir una propiedad de dominio de almacenamiento personalizado.|Una propiedad de dominio almacenada en otras partes del modelo o externamente. Por ejemplo, podría analizar una cadena de expresión en un árbol en el modelo.|[Propiedades calculadas y de almacenamiento personalizado](../modeling/calculated-and-custom-storage-properties.md)|
|Invalidar controladores de los cambios como OnValueChanging y OnDeleting|Mantener sincronizados los elementos diferentes y mantener valores externos sincronizada con el modelo.<br /><br /> Restringir los valores a intervalos definidos.<br /><br /> Se llama inmediatamente antes y después el valor de propiedad y otros cambios. Puede finalizar el cambio iniciando una excepción.|[Controladores de los cambios de valor de propiedad de dominio](../modeling/domain-property-value-change-handlers.md)|
|Reglas|Puede definir reglas que se ponen en cola para la ejecución inmediatamente antes del final de una transacción en el que ha ocurrido un cambio. No se ejecutan en la operación de deshacer o rehacer. Puede usarlos para mantener sincronizadas con otra parte de la tienda.|[Las reglas propagan los cambios dentro del modelo](../modeling/rules-propagate-changes-within-the-model.md)|
|Eventos de Store|El almacén de modelado proporciona notificaciones de eventos, como agregar o eliminar un elemento o vínculo o cambiar el valor de una propiedad. El evento también se ejecuta en Deshacer y rehacer. Usar eventos de almacén para actualizar los valores que no están en el almacén.|[Los controladores de eventos propagan cambios fuera del modelo](../modeling/event-handlers-propagate-changes-outside-the-model.md)|
|Eventos de .NET|Las formas tienen controladores de eventos que responden a clics del mouse y otros movimientos. Tendrá que registrar estos eventos para cada objeto. El registro se suele realizar en un reemplazo de InitializeInstanceResources y debe realizarse para cada elemento.<br /><br /> Normalmente, estos eventos se producen fuera de una transacción.|[Cómo: Interceptar un clic en una forma o un elemento Decorator](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)|
|Reglas de límites|Una regla de límites se utiliza específicamente para restringir los límites de una forma.|[Ubicación y tamaño de las reglas de restricción de formas BoundsRules](/visualstudio/modeling/boundsrules-constrain-shape-location-and-size?view=vs-2015)|
|Reglas de selección|Las reglas de selección restringen específicamente el usuario puede seleccionar.|[Cómo: Acceder a la selección actual y restringirla](../modeling/how-to-access-and-constrain-the-current-selection.md)|
|OnAssocatedPropertyChanged|Indicar estados de los elementos del modelo mediante las características de las formas y conectores como instantáneas, las puntas de flecha, color y los anchos de línea y estilo.|[Actualizar formas y conectores para reflejar el modelo](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)|

## <a name="comparing-rules-and-store-events"></a>**Comparación de las reglas y eventos de Store**
 Cambio notificadores, reglas y los eventos se ejecutan cuando se producen cambios en un modelo.

 Normalmente, se aplican las reglas en la transacción final en el que se ha producido el cambio y los eventos se aplican después de confirmados los cambios en una transacción.

 Usar eventos de almacén para sincronizar el modelo con objetos fuera de Store y las reglas para mantener la coherencia en el Store.

- **Crear reglas personalizadas** crear una regla personalizada como una clase derivada de una regla de abstracta. También debe notificar al marco acerca de la regla personalizada. Para obtener más información, consulte [propagar cambios en el modelo de reglas de](../modeling/rules-propagate-changes-within-the-model.md).

- **Suscribirse a eventos** para poder suscribirse a un evento, cree un controlador de eventos y el delegado. A continuación, utilice el <xref:Microsoft.VisualStudio.Modeling.Store.EventManagerDirectory%2A>propiedad para suscribirse al evento. Para obtener más información, consulte [controladores propagar los cambios fuera el modelo de evento](../modeling/event-handlers-propagate-changes-outside-the-model.md).

- **Deshaciendo cambios** al deshacer una transacción, se generan eventos, pero no se aplican las reglas. Si una regla cambia un valor y deshacer el cambio, el valor se restablece al valor original durante la acción de deshacer. Cuando se genera un evento, debe cambiar manualmente el valor a su valor original. Para obtener más información acerca de las transacciones y deshacer, vea [Cómo: Usar transacciones para actualizar el modelo](../modeling/how-to-use-transactions-to-update-the-model.md).

- **Pasar argumentos de evento para eventos y reglas** ambos eventos y las reglas se pasan un `EventArgs` parámetro que tiene información acerca de cómo puede cambiar el modelo.

## <a name="see-also"></a>Vea también

- [Cómo: Interceptar un clic en una forma o un elemento Decorator](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)
- [Escribir código para personalizar un lenguaje específico de dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)
