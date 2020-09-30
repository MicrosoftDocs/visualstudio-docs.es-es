---
title: Responder a los cambios y propagarlos
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 96342abce736f18d79f89b9441d9b53c068cbecf
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2020
ms.locfileid: "91583897"
---
# <a name="respond-to-and-propagate-changes"></a>Responder a los cambios y propagarlos

Cuando un elemento se crea, se elimina o se actualiza, se puede escribir código que propague el cambio a otras partes del modelo o a recursos externos como archivos, bases de datos u otros componentes.

## <a name="reference"></a>Referencia

Como norma general, tenga en cuenta estas técnicas en el orden siguiente:

|Técnica|Escenarios|Para obtener más información|
|-|-|-|
|Defina una propiedad de dominio calculado.|Propiedad de dominio cuyo valor se calcula a partir de otras propiedades del modelo. Por ejemplo, un precio que es la suma de los precios de los elementos relacionados.|[Propiedades calculadas y de almacenamiento personalizado](../modeling/calculated-and-custom-storage-properties.md)|
|Defina una propiedad de dominio de almacenamiento personalizada.|Propiedad de dominio almacenada en otras partes del modelo o externamente. Por ejemplo, puede analizar una cadena de expresión en un árbol del modelo.|[Propiedades calculadas y de almacenamiento personalizado](../modeling/calculated-and-custom-storage-properties.md)|
|Invalidar controladores de cambios como OnValueChanging y eliminar|Mantenga los distintos elementos sincronizados y mantenga los valores externos sincronizados con el modelo.<br /><br /> Restrinja los valores a los intervalos definidos.<br /><br /> Se llama inmediatamente antes y después del valor de la propiedad y otros cambios. Puede finalizar el cambio iniciando una excepción.|[Controladores de los cambios de valor de propiedad de dominio](../modeling/domain-property-value-change-handlers.md)|
|Reglas|Puede definir reglas que se ponen en cola para su ejecución justo antes del final de una transacción en la que se ha producido un cambio. No se ejecutan en las acciones de deshacer o rehacer. Úselos para mantener una parte del almacén sincronizada con otra.|[Las reglas propagan los cambios dentro del modelo](../modeling/rules-propagate-changes-within-the-model.md)|
|Almacenar eventos|El almacén de modelado proporciona notificaciones de eventos como agregar o eliminar un elemento o vínculo, o cambiar el valor de una propiedad. El evento también se ejecuta en las acciones de deshacer y rehacer. Utilice eventos de almacén para actualizar los valores que no están en el almacén.|[Los controladores de eventos propagan cambios fuera del modelo](../modeling/event-handlers-propagate-changes-outside-the-model.md)|
|Eventos .NET|Las formas tienen controladores de eventos que responden a los clics del mouse y otros gestos. Debe registrarse para estos eventos para cada objeto. El registro se realiza normalmente en una invalidación de InitializeInstanceResources y se debe hacer para cada elemento.<br /><br /> Normalmente, estos eventos se producen fuera de una transacción.|[Cómo: Interceptar un clic en una forma o decorador](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)|
|Reglas de límites|Una regla de límites se usa específicamente para restringir los límites de una forma.|[Ubicación y tamaño de las reglas de restricción de formas BoundsRules](../vs-2015/modeling/boundsrules-constrain-shape-location-and-size.md?view=vs-2015&preserve-view=true)|
|Reglas de selección|Las reglas de selección restringen específicamente lo que el usuario puede seleccionar.|[Cómo: Tener acceso y restringir una selección](../modeling/how-to-access-and-constrain-the-current-selection.md)|
|OnAssocatedPropertyChanged|Indicar los Estados de los elementos de modelo mediante características de formas y conectores, como sombra, puntas de flecha, color y ancho de línea y estilo.|[Actualizar formas y conectores para reflejar el modelo](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)|

## <a name="compare-rules-and-store-events"></a>Comparar reglas y almacenar eventos

Los notificadores de cambio, las reglas y los eventos se ejecutan cuando se producen cambios en un modelo.

Normalmente, las reglas se aplican a la transacción final en la que se ha producido el cambio y los eventos se aplican después de que se confirmen los cambios en una transacción.

Utilice eventos de almacén para sincronizar el modelo con objetos fuera del almacén y reglas para mantener la coherencia dentro del almacén.

- **Creación de reglas personalizadas** Puede crear una regla personalizada como una clase derivada a partir de una regla abstracta. También debe notificar al marco de trabajo la regla personalizada. Para obtener más información, vea [propagar los cambios dentro del modelo](../modeling/rules-propagate-changes-within-the-model.md).

- **Suscribirse a eventos** Para poder suscribirse a un evento, cree un controlador de eventos y un delegado. A continuación, utilice la <xref:Microsoft.VisualStudio.Modeling.Store.EventManagerDirectory%2A> propiedad para suscribirse al evento. Para obtener más información, vea [los controladores de eventos propagan los cambios fuera del modelo](../modeling/event-handlers-propagate-changes-outside-the-model.md).

- **Deshacer cambios** Al deshacer una transacción, se generan eventos, pero no se aplican las reglas. Si una regla cambia un valor y se deshace ese cambio, el valor se restablece al valor original durante la acción de deshacer. Cuando se produce un evento, debe volver a cambiar manualmente el valor a su valor original. Para obtener más información acerca de las transacciones y deshacer, consulte [Cómo: usar transacciones para actualizar el modelo](../modeling/how-to-use-transactions-to-update-the-model.md).

- **Pasar argumentos de evento a reglas y eventos** A los eventos y las reglas se les pasa un `EventArgs` parámetro con información sobre cómo cambió el modelo.

## <a name="see-also"></a>Vea también

- [Cómo: Interceptar un clic en una forma o decorador](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)
- [Escribir código para personalizar lenguajes específicos de dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)