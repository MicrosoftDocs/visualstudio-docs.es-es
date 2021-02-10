---
title: Configurar destinos y tareas | Microsoft Docs
description: Configure los destinos y las tareas de MSBuild para que se ejecuten en modo inactivo con MSBuild y así poder tener como destinos contextos diferentes del que se está ejecutando.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9aabe67a-1720-4bbf-80d3-822b3ccf75c0
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5548478e5404c69acc92d7ca7dc4deb6a2e29fdf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922542"
---
# <a name="configure-targets-and-tasks"></a>Configurar destinos y tareas

Puede configurar los destinos y las tareas de MSBuild para que se ejecuten en modo inactivo con MSBuild y así poder tener como destinos contextos diferentes del que se está ejecutando. Por ejemplo, puede tener como destino una aplicación de 32 bits de .NET Framework 2.0 mientras el equipo de desarrollo se ejecuta en un sistema operativo de 64 bits de .NET Framework 4.5. El destino también pueden ser equipos que se ejecuten con .NET Framework 4 o versiones anteriores. La combinación del valor de bits 32 o 64 y la versión específica de .NET Framework se denomina *contexto de destino*.

## <a name="installation"></a>Instalación

  Si quiere instalar MSBuild independientemente de Visual Studio, puede descargar el paquete de instalación desde la página de [descarga de MSBuild](https://www.microsoft.com/download/details.aspx?id=40760). También debe instalar las versiones de .NET Framework que quiera usar.

## <a name="targets-and-tasks"></a>Destinos y tareas

 MSBuild ejecuta determinadas tareas de compilación en modo inactivo para poder establecer como destino un conjunto de contextos más grande.  Por ejemplo, MSBuild de 32 bits puede ejecutar una tarea de compilación en un proceso de 64 bits para poder ejecutarse en un equipo de 64 bits. Esto lo controlan los argumentos `UsingTask` y los parámetros `Task`. Los destinos instalados por .NET Framework 4.5 establecen estos argumentos y parámetros, y no se requiere ningún cambio para compilar aplicaciones para los distintos contextos de destino.

 Si desea crear su propio contexto de destino, debe establecer correctamente estos argumentos y parámetros. Vea ejemplos en los archivos *Microsoft.Common.targets* y *Microsoft.Common.Tasks* de .NET Framework 4.5.  Para obtener información sobre cómo crear una tarea personalizada que trabaje con varios contextos de destino, o cómo modificar tareas existentes, vea [Cómo: Configurar destinos y tareas](../msbuild/how-to-configure-targets-and-tasks.md).

## <a name="see-also"></a>Vea también

- [Compatibilidad con múltiples versiones (multi-targeting)](../msbuild/msbuild-multitargeting-overview.md)
