---
title: Generación de perfiles y seguridad en Windows Vista | Microsoft Docs
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,security
- performance tools, security
ms.assetid: 842112fc-b886-4801-8cd7-a25b314b0393
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2a74862d59fe402cbfd9e6bfa804d62ca4c8310b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778380"
---
# <a name="profiling-and-windows-vista-security"></a>Generación de perfiles y seguridad en Windows Vista

En función de la configuración de los permisos de acceso de usuario de [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)] que haya facilitado un administrador de equipo, un usuario puede tener permisos de seguridad para generar perfiles de un proceso en ese equipo. En los siguientes ejemplos se muestran las posibles diferencias existentes entre los usuarios:

- Algunos usuarios pueden tener acceso a las características avanzadas de generación de perfiles cuando el administrador ha configurado el controlador y el servicio para que se inicien.

- Los usuarios de dominio pueden tener acceso solo a la generación de perfiles de ejemplo.

- Algunos usuarios pueden denegar el acceso a la generación de perfiles a todos los demás usuarios.

  Para obtener más información, consulte las opciones ADMIN de [VSPerfCmd](../profiling/vsperfcmd.md).

## <a name="cross-session-profiling"></a>Generación de perfiles entre sesiones

La *generación de perfiles entre sesiones* es la capacidad de generar perfiles de un proceso que se ejecuta en otra sesión de usuario. Por ejemplo, la mayoría de los servicios se ejecutan en la sesión 0, pero los usuarios no pueden ejecutarse directamente en la sesión 0. Con el botón **Adjuntar al proceso** de la barra de herramientas del Explorador de rendimiento, o la opción `/attach` de la herramienta de línea de comandos VSPerfCmd, puede generar perfiles de la mayoría de los procesos en otras sesiones de usuario.

Puede ver una lista de los procesos que están disponibles mediante el establecimiento de las opciones de visibilidad de generación de perfiles entre procesos. Estas opciones están disponibles en la ventana **Adjuntar al proceso**, que aparece al seleccionar **Adjuntar al proceso**:

- **Mostrar los procesos de todos los usuarios**

  Cuando esta opción no está seleccionada, la lista solo muestra los procesos que pertenecen al usuario actual. De lo contrario, la lista muestra los procesos de todos los usuarios.

- **Mostrar los procesos de todas las sesiones**

  Cuando esta opción no está seleccionada, la lista muestra los procesos de la sesión actual. De lo contrario, la lista muestra los procesos de todas las sesiones.

## <a name="see-also"></a>Vea también

- [Información general](../profiling/overviews-performance-tools.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Cómo: Conectar a procesos en ejecución](/previous-versions/visualstudio/visual-studio-2010/c6wf8e4z\(v\=vs.100\))
