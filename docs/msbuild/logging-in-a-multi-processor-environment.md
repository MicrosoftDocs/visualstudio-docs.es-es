---
title: Registrar en un entorno de varios procesadores | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, multi-processor logging
- MSBuild, logging
ms.assetid: dd4dae65-ed04-4883-b48d-59bcb891c4dc
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 65f0558e26583961d94ce380b59a60ecca45987b
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578525"
---
# <a name="logging-in-a-multi-processor-environment"></a>Registrar en un entorno de varios procesadores
La capacidad de MSBuild para usar varios procesadores puede reducir significativamente el tiempo de compilación de los proyectos, pero también agrega complejidad al proceso de registro. En un entorno de un solo procesador, el registrador puede administrar eventos de entrada, mensajes, advertencias y errores de una manera predecible y secuencial. Sin embargo, en un entorno de varios procesadores, los eventos de varios orígenes pueden llegar simultáneamente o desordenados. MSBuild dispone de un nuevo registrador para varios procesadores y habilita la creación de "registradores de reenvío" personalizados.

## <a name="log-multiple-processor-builds"></a>Registrar compilaciones de varios procesadores
Cuando se compilan uno o varios proyectos en un sistema de varios procesadores o varios núcleos, los eventos de compilación de MSBuild de todos los proyectos se generan simultáneamente. Es posible que llegue una avalancha de datos de eventos al registrador al mismo tiempo o que vengan desordenados. Esto puede sobrecargar el registrador y producir un aumento del tiempo de compilación, una salida incorrecta del registrador o incluso la interrupción de una compilación. Para resolver estos problemas, el registrador de MSBuild puede procesar eventos desordenados y asociar los eventos y sus orígenes.

Puede mejorar más la eficacia del registro creando un registrador de reenvío personalizado. Un registrador de reenvío personalizado actúa como filtro que le permite elegir, antes de compilar, los eventos que desea supervisar. Cuando se utiliza un registrador de reenvío personalizado, los eventos no deseados no sobrecargan el registrador, desordenan los registros ni ralentizan el tiempo de compilación.

### <a name="central-logging-model"></a>Modelo de registro central
Para compilaciones de varios procesadores, MSBuild utiliza un "modelo de registro central". En el modelo de registro central, una instancia de *MSBuild.exe* actúa como proceso de compilación principal o "nodo central". Las instancias secundarias de *MSBuild.exe*, o "nodos secundarios", se asocian al nodo central. Los registradores basados en ILogger asociados al nodo central se conocen como "registradores centrales" y los registradores asociados a los nodos secundarios se conocen como "registradores secundarios".

Cuando se realiza una compilación, los registradores secundarios enrutan su tráfico de eventos a los registradores centrales. Debido a que los eventos se originan en varios nodos secundarios, los datos llegan al nodo central simultáneamente pero intercalados. Para resolver las referencias entre eventos y proyectos y entre eventos y destinos, los argumentos de evento incluyen la información contextual adicional acerca del evento de compilación.

Aunque sólo es necesario que el registrador central implemente <xref:Microsoft.Build.Framework.ILogger>, es recomendable que también implemente <xref:Microsoft.Build.Framework.INodeLogger> si desea que el registrador central se inicialice con el número de nodos que están participando en la compilación. Se invoca la siguiente sobrecarga del método <xref:Microsoft.Build.Framework.ILogger.Initialize%2A> cuando el motor inicializa el registrador:

```csharp
public interface INodeLogger: ILogger
{
    public void Initialize(IEventSource eventSource, int nodeCount);
}
```

### <a name="distributed-logging-model"></a>Modelo de registro distribuido
En el modelo de registro central, un tráfico excesivo de mensajes entrantes, como cuando se compilan muchos proyectos al mismo tiempo, puede sobrecargar el nodo central, saturando el sistema y disminuyendo el rendimiento de la compilación.

Para reducir este problema, MSBuild habilita también un "modelo de registro distribuido" que amplía el modelo de registro central permitiendo crear registradores de reenvío. Un registrador de reenvío se asocia a un nodo secundario y recibe los eventos de compilación entrantes de ese nodo. El registrador de reenvío es como un registrador normal sólo que puede filtrar los eventos y, a continuación, reenviar sólo los deseados al nodo central. De esta manera se reduce el tráfico de mensajes en el nodo central y, por consiguiente, habilita la mejora del rendimiento.

 Para crear un registrador de reenvío, puede implementar la interfaz <xref:Microsoft.Build.Framework.IForwardingLogger>, derivada de <xref:Microsoft.Build.Framework.ILogger>. La interfaz se define como:

```csharp
public interface IForwardingLogger: INodeLogger
{
    public IEventRedirector EventRedirector { get; set; }
    public int NodeId { get; set; }
}
```

Para reenviar los eventos de un registrador de reenvío, llame al método <xref:Microsoft.Build.Framework.IEventRedirector.ForwardEvent%2A> de la interfaz <xref:Microsoft.Build.Framework.IEventRedirector>. Pase el <xref:Microsoft.Build.Framework.BuildEventArgs> adecuado, o un derivado, como parámetro.

Para obtener más información, vea [Crear registradores de reenvío](../msbuild/creating-forwarding-loggers.md).

### <a name="attaching-a-distributed-logger"></a>Asociar un registrador distribuido
Para asociar un registrador distribuido en una compilación de la línea de comandos, utilice el modificador `-distributedlogger` (o, `-dl` abreviado). El formato para especificar los nombres de los tipos y clases del registrador es igual que el del modificador `-logger`, sólo que un registrador distribuido consta de dos clases de registro: un registrador de reenvío y un registrador central. A continuación, se muestra un ejemplo de cómo asociar un registrador distribuido:

```cmd
msbuild.exe *.proj -distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,
Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,
Culture=neutral
```

Un asterisco (*) separa los dos nombres de registrador en el modificador `-dl`.

## <a name="see-also"></a>Vea también
- [Registradores de compilación](../msbuild/build-loggers.md)
- [Crear registradores de reenvío](../msbuild/creating-forwarding-loggers.md)
