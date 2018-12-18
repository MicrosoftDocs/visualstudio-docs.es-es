---
title: Configurar destinos y tareas | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
ms.assetid: 9aabe67a-1720-4bbf-80d3-822b3ccf75c0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b6075eea96d217b029f7febb8bcf80aef2a47eb2
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/19/2018
ms.locfileid: "39151150"
---
# <a name="configure-targets-and-tasks"></a>Configurar destinos y tareas
Puede configurar los destinos y las tareas de MSBuild para que se ejecuten en modo inactivo con MSBuild y así poder tener como destinos contextos diferentes del que se está ejecutando. Por ejemplo, puede tener como destino una aplicación de 32 bits de .NET Framework 2.0 mientras el equipo de desarrollo se ejecuta en un sistema operativo de 64 bits de .NET Framework 4.5. El destino también pueden ser equipos que se ejecuten con .NET Framework 4 o versiones anteriores. La combinación del valor de bits 32 o 64 y la versión específica de .NET Framework se denomina *contexto de destino*.  
  
## <a name="installation"></a>Instalación  
 .NET Framework 4.5 y 4.5.1 reemplazan el Common Language Runtime (CLR), los destinos, las tareas y las herramientas de .NET Framework 4 sin cambiarles el nombre. .NET Framework 4.5.1 se instala como parte de [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)].  
  
 Si quiere instalar MSBuild independientemente de Visual Studio, puede descargar el paquete de instalación desde la página de [descarga de MSBuild](http://go.microsoft.com/fwlink/?LinkId=309745). También debe instalar las versiones de .NET Framework que quiera usar.  
  
## <a name="targets-and-tasks"></a>Destinos y tareas  
 MSBuild ejecuta determinadas tareas de compilación en modo inactivo para poder establecer como destino un conjunto de contextos más grande.  Por ejemplo, MSBuild de 32 bits puede ejecutar una tarea de compilación en un proceso de 64 bits para poder ejecutarse en un equipo de 64 bits. Esto lo controlan los argumentos `UsingTask` y los parámetros `Task`. Los destinos instalados por .NET Framework 4.5 establecen estos argumentos y parámetros, y no se requiere ningún cambio para compilar aplicaciones para los distintos contextos de destino.  
  
 Si desea crear su propio contexto de destino, debe establecer correctamente estos argumentos y parámetros. Vea ejemplos en los archivos *Microsoft.Common.targets* y *Microsoft.Common.Tasks* de .NET Framework 4.5.  Para obtener información sobre cómo crear una tarea personalizada que trabaje con varios contextos de destino o sobre cómo modificar tareas existentes, vea [Cómo: Configurar destinos y tareas](../msbuild/how-to-configure-targets-and-tasks.md).  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con múltiples versiones (multi-targeting)](../msbuild/msbuild-multitargeting-overview.md)