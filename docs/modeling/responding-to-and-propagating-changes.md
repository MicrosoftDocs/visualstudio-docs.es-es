---
title: "Responder a los cambios y propagarlos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Lenguaje específico de dominio, eventos"
ms.assetid: fc2e9ac5-7a84-44ed-9945-94e45f89c227
caps.latest.revision: 24
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 24
---
# Responder a los cambios y propagarlos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cuando se crea, se elimina o actualiza un elemento, puede escribir código que propaga el cambio a otras partes del modelo, o a los recursos externos como archivos, bases de datos, u otros componentes.  
  
## En esta sección  
 como instrucción, considere estas técnicas en el orden siguiente:  
  
|Técnica|Escenarios|Para obtener más información|  
|-------------|----------------|----------------------------------|  
|Defina una propiedad calculada del dominio.|Una propiedad de dominio cuyo valor se calcula de otras propiedades del modelo.  Por ejemplo, un precio que es la suma de los precios de elementos relacionados.|[Propiedades de almacenamiento personalizados y calculados](../modeling/calculated-and-custom-storage-properties.md)|  
|Defina una propiedad personalizada del dominio de almacenamiento.|Una propiedad de dominio almacenada en otras partes del modelo o externamente.  Por ejemplo, puede analizar una cadena de expresión en un árbol del modelo.|[Propiedades de almacenamiento personalizados y calculados](../modeling/calculated-and-custom-storage-properties.md)|  
|Reemplace los controladores de cambio como OnValueChanging y OnDeleting|Mantenga diferentes elementos de la sincronización, y mantener los valores externos en sincronización con el modelo.<br /><br /> Limita los valores a intervalos definidos.<br /><br /> Denominado inmediatamente antes y después del valor de propiedad y de otros cambios.  Puede finalizar el cambio iniciando una excepción.|[Controladores de los cambios de valor de propiedad de dominio](../modeling/domain-property-value-change-handlers.md)|  
|Reglas|Puede definir reglas que se ponen en la cola para la ejecución justo antes del final de una transacción en la que un cambio ha sucedido.  No se ejecutan en deshacer o rehacer.  Utilícelos para conservar una parte del almacén en para sincronizar con otra.|[Reglas de propagan los cambios en el modelo](../modeling/rules-propagate-changes-within-the-model.md)|  
|Eventos de almacén|El almacén de modelado proporciona notificaciones de eventos como agregar o eliminar un elemento o un vínculo, o cambiar el valor de una propiedad.  El evento también se ejecuta en deshacer y rehacer.  el uso almacena eventos para actualizar los valores que no están en el almacén.|[Los controladores de eventos propagan cambios fuera del modelo](../modeling/event-handlers-propagate-changes-outside-the-model.md)|  
|eventos de .NET|Las formas tienen controladores de eventos que respondan al mouse haga clic y otro los gestos.  Tiene que registrar para estos eventos para cada objeto.  El registro suele hacerse en un reemplazo de InitializeInstanceResources, y debe hacer para cada elemento.<br /><br /> Estos eventos se producen normalmente fuera de una transacción.|[Cómo: Interceptar un clic en una forma o decorador](../Topic/How%20to:%20Intercept%20a%20Click%20on%20a%20Shape%20or%20Decorator.md)|  
|reglas de los límites|Una regla de los límites se utiliza específicamente para restringir los límites de una forma.|[Ubicación y tamaño de las reglas de restricción de formas BoundsRules](../modeling/boundsrules-constrain-shape-location-and-size.md)|  
|reglas de selección|Las reglas de selección restringir específicamente lo que el usuario puede seleccionar.|[Cómo: Tener acceso y restringir una selección](../modeling/how-to-access-and-constrain-the-current-selection.md)|  
|OnAssocatedPropertyChanged|Indica los estados del modelo de elementos mediante características de formas y conectores como sombra, puntas de flecha, color, y los anchos de línea y estilo.|[Actualizar formas y conectores para reflejar el modelo](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)|  
  
## **comparar reglas y eventos almacenados**  
 Cambie los notificadores, reglas, y se ejecutan los eventos cuando se producen cambios en un modelo.  
  
 Las reglas se aplican normalmente en la transacción del final de la que el cambio ha producido, y se aplican los eventos después de los cambios en una transacción se confirman.  
  
 El uso almacena eventos para sincronizar el modelo con los objetos fuera del almacén, y reglas de mantener la coherencia dentro del almacén.  
  
-   **Crear reglas personalizadas** Se crean una regla personalizada como una clase derivada de una regla abstracta.  También debe notificar el marco sobre la regla personalizada.  Para obtener más información, vea [Reglas de propagan los cambios en el modelo](../modeling/rules-propagate-changes-within-the-model.md).  
  
-   **Suscribiéndose a eventos** Antes puede suscribirse a un evento, crear un controlador de eventos y un delegado.  Después utilice la propiedad de <xref:Microsoft.VisualStudio.Modeling.Store.EventManagerDirectory%2A>para suscribirse al evento.  Para obtener más información, vea [Los controladores de eventos propagan cambios fuera del modelo](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
-   **El deshacer cambia** Al deshacer una transacción, se generan los eventos, pero las reglas no se aplican.  Si una regla cambia un valor y deshace que cambie, el valor se restablece el valor original durante la acción de deshacer.  Cuando se produce un evento, debe cambiar manualmente el valor de a su valor original.  Para obtener más información sobre transactons y deshacer, vea [Cómo: Usar transacciones para actualizar el modelo](../modeling/how-to-use-transactions-to-update-the-model.md).  
  
-   **Pasar argumentos a las reglas y** los eventos y las reglas del caso**de los eventos** se pasa un parámetro de `EventArgs` que contiene información sobre cómo el modelo modificado.  
  
## Vea también  
 [Cómo: Interceptar un clic en una forma o decorador](../Topic/How%20to:%20Intercept%20a%20Click%20on%20a%20Shape%20or%20Decorator.md)   
 [Escribir código para personalizar un lenguaje específico de dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)