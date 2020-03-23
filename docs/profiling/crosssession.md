---
title: CrossSession | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b9fcb9c3-7903-478c-9b7c-dbd94092fcba
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 06de982643a08e1af88073dde0fb0a9abc029900
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779459"
---
# <a name="crosssession"></a>CrossSession
La opción **CrossSession** de *VSPerfCmd.exe* permite que el generador de perfiles recopile datos de cualquier sesión de consola. La opción **CrossSession** debe usarse con la opción **Start**.

 Puede usar la abreviatura **CS** en lugar de **CrossSession**.

## <a name="syntax"></a>Sintaxis

```cmd
VSPerfCmd.exe /Start:Method /CrossSession [Options]
```

#### <a name="parameters"></a>Parámetros
 None

## <a name="valid-options"></a>Opciones válidas
 Para habilitar la generación de perfiles en otra sesión, la opción **CrossSession** debe especificarse con la opción **Start**. También debe especificarse **CrossSession** en todos los comandos **VSPerfCmd Attach** y **Detach** posteriores.

 **Start:** `Method` La opción **Start** inicializa el generador de perfiles en el método de generación de perfiles especificado.

 **Attach:** _PID_[ **,** _PID_] Inicia la generación de perfiles de los procesos especificados.

 **Detach**[ **:** _PID_[,_PID_]] Detiene la generación de perfiles de los procesos especificados.

## <a name="example"></a>Ejemplo
 En este ejemplo, se usa la opción **CrossSession** para adjuntar a una aplicación que se ha iniciado en otra sesión de consola.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /CrossSession
VSPerfCmd.exe /Attach:12345 /CS
```

## <a name="see-also"></a>Vea también
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Generar perfiles de aplicaciones independientes](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Generación de perfiles de aplicaciones web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Generar perfiles para servicios](../profiling/command-line-profiling-of-services.md)
