---
title: Responder a los cambios y propagarlos
description: Aprenda que cuando se crea, elimina o actualiza un elemento, puede escribir código que propague el cambio a otras partes del modelo o a recursos externos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d6fc8345ca90414f410dde9a089d9529ed19536b
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387585"
---
# <a name="respond-to-and-propagate-changes"></a>Respuesta y propagación de cambios

Cuando se crea, elimina o actualiza un elemento, puede escribir código que propague el cambio a otras partes del modelo o a recursos externos como archivos, bases de datos u otros componentes.

## <a name="reference"></a>Referencia

Como guía, tenga en cuenta estas técnicas en el orden siguiente:

|Técnica|Escenarios|Para obtener más información|
|-|-|-|
|Defina una propiedad de dominio calculado.|Propiedad de dominio cuyo valor se calcula a partir de otras propiedades del modelo. Por ejemplo, un precio que es la suma de los precios de los elementos relacionados.|[Propiedades calculadas y de almacenamiento personalizado](../modeling/calculated-and-custom-storage-properties.md)|
|Defina una propiedad de dominio de almacenamiento personalizado.|Propiedad de dominio almacenada en otras partes del modelo o externamente. Por ejemplo, podría analizar una cadena de expresión en un árbol del modelo.|[Propiedades calculadas y de almacenamiento personalizado](../modeling/calculated-and-custom-storage-properties.md)|
|Invalidar controladores de cambios como OnValueChanging y OnDeleting|Mantenga los distintos elementos sincronizados y mantenga los valores externos sincronizados con el modelo.<br /><br /> Restringir valores a intervalos definidos.<br /><br /> Se llama inmediatamente antes y después del valor de propiedad y otros cambios. Puede finalizar el cambio iniciando una excepción.|[Controladores de los cambios de valor de propiedad de dominio](../modeling/domain-property-value-change-handlers.md)|
|Reglas|Puede definir reglas que se ponen en cola para su ejecución justo antes del final de una transacción en la que se ha producido un cambio. No se ejecutan en Deshacer o Rehacer. Úsenlos para mantener sincronizada una parte del almacén con otra.|[Las reglas propagan los cambios dentro del modelo](../modeling/rules-propagate-changes-within-the-model.md)|
|Almacenar eventos|El almacén de modelado proporciona notificaciones de eventos como agregar o eliminar un elemento o vínculo, o cambiar el valor de una propiedad. El evento también se ejecuta en Deshacer y Rehacer. Use eventos de almacén para actualizar los valores que no están en el almacén.|[Los controladores de eventos propagan cambios fuera del modelo](../modeling/event-handlers-propagate-changes-outside-the-model.md)|
|Eventos de .NET|Las formas tienen controladores de eventos que responden a clics del mouse y otros gestos. Debe registrarse para estos eventos para cada objeto. El registro se realiza normalmente en una invalidación de InitializeInstanceResources y debe realizarse para cada elemento.<br /><br /> Estos eventos suelen producirse fuera de una transacción.|[Cómo: Interceptar un clic en una forma o decorador](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)|
|Reglas de límites|Una regla de límites se usa específicamente para restringir los límites de una forma.|[Ubicación y tamaño de las reglas de restricción de formas BoundsRules](/previous-versions/visualstudio/visual-studio-2015/modeling/boundsrules-constrain-shape-location-and-size?preserve-view=true&view=vs-2015)|
|Reglas de selección|Las reglas de selección restringen específicamente lo que el usuario puede seleccionar.|[Cómo: Tener acceso y restringir una selección](../modeling/how-to-access-and-constrain-the-current-selection.md)|
|OnAssocatedPropertyChanged|Indique los estados de los elementos del modelo mediante características de formas y conectores como sombras, puntas de flecha, colores y anchos de línea y estilo.|[Actualizar formas y conectores para reflejar el modelo](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)|

## <a name="compare-rules-and-store-events"></a>Comparación de reglas y almacenamiento de eventos

Los notificadores de cambios, las reglas y los eventos se ejecutan cuando se producen cambios en un modelo.

Normalmente, las reglas se aplican en la transacción final en la que se ha producido el cambio y los eventos se aplican después de que se confirman los cambios en una transacción.

Use eventos de almacén para sincronizar el modelo con objetos fuera de Store y reglas para mantener la coherencia dentro de Store.

- **Creación de reglas personalizadas** Una regla personalizada se crea como una clase derivada a partir de una regla abstracta. También debe notificar al marco sobre la regla personalizada. Para obtener más información, vea [Reglas propagar cambios dentro del modelo](../modeling/rules-propagate-changes-within-the-model.md).

- **Suscripción a eventos** Para poder suscribirse a un evento, cree un controlador de eventos y un delegado. A continuación, <xref:Microsoft.VisualStudio.Modeling.Store.EventManagerDirectory%2A> use la propiedad para suscribirse al evento. Para obtener más información, vea [Controladores de eventos propagar cambios fuera del modelo](../modeling/event-handlers-propagate-changes-outside-the-model.md).

- **Deshacer cambios** Al deshacer una transacción, se genera un evento, pero no se aplican reglas. Si una regla cambia un valor y se deshace ese cambio, el valor se restablece al valor original durante la acción de deshacer. Cuando se genera un evento, debe cambiar manualmente el valor a su valor original. Para obtener más información sobre las transacciones y deshacer, [vea Cómo: Usar transacciones para actualizar el modelo.](../modeling/how-to-use-transactions-to-update-the-model.md)

- **Pasar argumentos de evento a reglas y eventos** Tanto los eventos como las reglas se pasan a `EventArgs` un parámetro que tiene información sobre cómo cambió el modelo.

## <a name="see-also"></a>Vea también

- [Cómo: Interceptar un clic en una forma o decorador](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)
- [Escribir código para personalizar un lenguaje Domain-Specific personalizado](../modeling/writing-code-to-customise-a-domain-specific-language.md)