---
title: Escribir registradores que reconocen varios procesadores | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- msbuild, multi-proc aware loggers
- multi-proc loggers
- loggers, multi-proc
ms.assetid: ff987d1b-1798-4803-9ef6-cc8fcc263516
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 486c8e32b577b6c794a03c080a909023b40eafde
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49219967"
---
# <a name="writing-multi-processor-aware-loggers"></a>Escribir registradores que reconocen varios procesadores
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
La capacidad de [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] para aprovechar las ventajas de varios procesadores puede disminuir el tiempo de compilación de los proyectos, pero también agrega complejidad al registro de eventos de compilación. En un entorno de un solo procesador, los eventos, mensajes, advertencias y errores llegan al registrador de una manera predecible y secuencial. Sin embargo, en un entorno de varios procesadores, pueden llegar eventos de orígenes diferentes al mismo tiempo o desordenados. Para solucionar este asunto, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] dispone de un registrador que reconoce varios procesadores y un nuevo modelo de registro, y permite crear "registradores de reenvío" personalizados.  
  
## <a name="multi-processor-logging-challenges"></a>Dificultades del registro de varios procesadores  
 Cuando se compilan uno o varios proyectos en un sistema de varios procesadores o varios núcleos, los eventos de compilación de [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] de todos los proyectos se generan al mismo tiempo. Es posible que llegue una avalancha de mensajes de eventos al registrador al mismo tiempo o desordenados. Debido a que el registrador de [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 2.0 no está diseñado para administrar esta situación, puede sobrecargar el registrador y provocar un aumento en el tiempo de compilación, resultados incorrectos del registrador o incluso la interrupción de una compilación. Para resolver estos problemas, el registrador (a partir de [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 3.5) puede procesar eventos desordenados y asociar los eventos y sus orígenes.  
  
 Puede mejorar más la eficacia del registro creando un registrador de reenvío personalizado. Un registrador de reenvío personalizado actúa como filtro que le permite elegir, antes de compilar, únicamente los eventos que desea supervisar. Cuando se utiliza un registrador de reenvío personalizado, los eventos no deseados no sobrecargan el registrador, desordenan los registros ni ralentizan el tiempo de compilación.  
  
## <a name="multi-processor-logging-models"></a>Modelos de registro para varios procesadores  
 Para solucionar los problemas de compilación para varios procesadores, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] admite dos modelos de registro, central y distribuido.  
  
### <a name="central-logging-model"></a>Modelo de registro central  
 En el modelo de registro central, una única instancia de MSBuild.exe actúa como "nodo central" y las instancias secundarias del nodo central ("nodos secundarios") se asocian al nodo central para ayudarle a realizar las tareas de compilación.  
  
 ![Modelo de registrador central](../msbuild/media/centralnode.png "CentralNode")  
  
 Los diferentes tipos de registradores que se asocian al nodo central se conocen como "registradores centrales". Sólo se puede asociar una instancia de cada tipo de registrador al nodo central al mismo tiempo.  
  
 Cuando se produce una compilación, los nodos secundarios enrutan sus eventos de compilación al nodo central. El nodo central enruta todos sus eventos y también los de los nodos secundarios, a uno o varios registradores centrales asociados. A continuación, los registradores crean archivos de registro basados en los datos entrantes.  
  
 Aunque sólo es necesario que el registrador central implemente <xref:Microsoft.Build.Framework.ILogger>, es recomendable que también implemente <xref:Microsoft.Build.Framework.INodeLogger> para que el registrador central se inicialice con el número de nodos que están participando en la compilación. Se invoca la siguiente sobrecarga del método <xref:Microsoft.Build.Framework.ILogger.Initialize%2A> cuando el motor inicializa el registrador.  
  
```  
public interface INodeLogger: ILogger  
{  
    public void Initialize(IEventSource eventSource, int nodeCount);  
}  
```  
  
 Los registradores basados en <xref:Microsoft.Build.Framework.ILogger> ya existentes pueden actuar como registradores centrales y asociarse a la compilación. Sin embargo, los registradores centrales escritos sin compatibilidad explícita para escenarios de registro de varios procesadores y los eventos desordenados podrían interrumpir una compilación o producir un resultado sin sentido.  
  
### <a name="distributed-logging-model"></a>Modelo de registro distribuido  
 En el modelo de registro central, un tráfico excesivo de mensajes entrantes puede sobrecargar el nodo central, como cuando se compilan muchos proyectos al mismo tiempo. Esto puede saturar los recursos del sistema y disminuir el rendimiento de la compilación. Para solucionar este problema, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] admite un modelo de registro distribuido.  
  
 ![Modelo de registro distribuido](../msbuild/media/distnode.png "DistNode")  
  
 El modelo de registro distribuido amplía el modelo de registro central y permite crear un registrador de reenvío.  
  
#### <a name="forwarding-loggers"></a>Registradores de reenvío  
 Un registrador de reenvío es un registrador secundario ligero que tiene un filtro de eventos que se asocia a un nodo secundario y recibe los eventos de compilación de entrada de ese nodo. Filtra los eventos de entrada y reenvía al nodo central sólo los que especifique. De esta manera se reduce el tráfico de mensajes que se envía al nodo central y mejora el rendimiento general de la compilación.  
  
 Hay dos maneras de utilizar el registro distribuido, como se indica a continuación:  
  
-   Personalizar el registrador de reenvío prefabricado denominado <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger>.  
  
-   Escribir su propio registrador de reenvío personalizado.  
  
 Puede modificar ConfigurableForwardingLogger para que se ajuste a sus necesidades. Para ello, llame al registrador en la línea de comandos mediante MSBuild.exe y enumere los eventos de compilación que desea que el registrador reenvíe al nodo central.  
  
 Otra opción es crear un registrador de reenvío personalizado. Creando un registrador de reenvío personalizado puede afinar el comportamiento del registrador. Sin embargo, crear un registrador de reenvío personalizado es más complejo que simplemente personalizar ConfigurableForwardingLogger. Para obtener más información, vea [Crear registradores de reenvío](../msbuild/creating-forwarding-loggers.md).  
  
## <a name="using-the-configurableforwardinglogger-for-simple-distributed-logging"></a>Utilizar ConfigurableForwardingLogger para el registro distribuido simple  
 Para asociar ConfigurableForwardingLogger o un registrador de reenvío personalizado, use el modificador `/distributedlogger` (`/dl` abreviado) en una compilación de línea de comandos de MSBuild.exe. El formato para especificar los nombres de los tipos y clases del registrador es igual que el del modificador `/logger`, sólo que un registrador distribuido siempre tiene dos clases de registro en lugar de una: el registrador de reenvío y el registrador central. A continuación, se muestra un ejemplo de cómo asociar un registrador de reenvío personalizado denominado XMLForwardingLogger.  
  
```  
msbuild.exe myproj.proj/distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,Culture=neutral  
```  
  
> [!NOTE]
>  Un asterisco (*) debe separar los dos nombres de registrador en el modificador `/dl`.  
  
 Usar ConfigurableForwardingLogger es como usar cualquier otro registrador (como se explica en [Obtener registros de compilación](../msbuild/obtaining-build-logs-with-msbuild.md)), solo que se asocia el registrador ConfigurableForwardingLogger en lugar del registrador de [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] típico, y se especifican como parámetros los eventos que quiere que ConfigurableForwardingLogger pase al nodo central.  
  
 Por ejemplo, si desea ser notificado únicamente cuando una compilación comienza y termina y cuando se produce un error, pasaría `BUILDSTARTEDEVENT`, `BUILDFINISHEDEVENT` y `ERROREVENT` como parámetros. Se puede pasar varios parámetros separándolos con punto y coma. A continuación, se muestra un ejemplo de cómo utilizar ConfigurableForwardingLogger para reenviar sólo los eventos `BUILDSTARTEDEVENT`, `BUILDFINISHEDEVENT` y `ERROREVENT`.  
  
```  
msbuild.exe myproj.proj /distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*ConfigureableForwardingLogger,C:\My.dll;BUILDSTARTEDEVENT; BUILDFINISHEDEVENT;ERROREVENT  
```  
  
 A continuación, se muestra una lista de los parámetros de ConfigurableForwardingLogger disponibles.  
  
|Parámetros de ConfigurableForwardingLogger|  
|---------------------------------------------|  
|BUILDSTARTEDEVENT|  
|BUILDFINISHEDEVENT|  
|PROJECTSTARTEDEVENT|  
|PROJECTFINISHEDEVENT|  
|TARGETSTARTEDEVENT|  
|TARGETFINISHEDEVENT|  
|TASKSTARTEDEVENT|  
|TASKFINISHEDEVENT|  
|ERROREVENT|  
|WARNINGEVENT|  
|HIGHMESSAGEEVENT|  
|NORMALMESSAGEEVENT|  
|LOWMESSAGEEVENT|  
|CUSTOMEVENT|  
|COMMANDLINE|  
|PERFORMANCESUMMARY|  
|NOSUMMARY|  
|SHOWCOMMANDLINE|  
  
## <a name="see-also"></a>Vea también  
 [Crear registradores de reenvío](../msbuild/creating-forwarding-loggers.md)



