---
title: 'Advertencia de seguridad: Adjuntar a un proceso que pertenezca a un usuario que no sea de confianza puede ser peligroso. Si la información siguiente le resulta sospechosa o no está seguro de su procedencia, no la adjunte a este proceso | Microsoft Docs'
ms.date: 1/15/2021
ms.topic: conceptual
f1_keywords:
- vs.debug.attachsecuritywarning
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 52246c1e-a371-40a0-b756-a435cc51876f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 44f7df253951d90a29c459bf28e6ff1c2279ee54
ms.sourcegitcommit: 7a5c4f60667b5792f876953d55192b49a73f5fe9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2021
ms.locfileid: "98533373"
---
# <a name="security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process"></a>Advertencia de seguridad: Adjuntar a un proceso que pertenezca a un usuario que no sea de confianza puede ser peligroso. Si la información siguiente le resulta sospechosa o no está seguro de su procedencia, no la adjunte a este proceso

Este cuadro de diálogo de advertencia aparece cuando se asocia a un proceso que contiene código de confianza parcial o que pertenece a un usuario que no es de confianza, inmediatamente antes de que ocurra la asociación. Un proceso que no es de confianza y que contiene código malintencionado puede dañar el equipo que lleva a cabo la depuración. Si existen razones para desconfiar del proceso, debe hacer clic en **Cancelar** para evitar la depuración.

En escenarios de IIS, es posible que se le muestre esta advertencia si usa un grupo de aplicaciones personalizado, que no se considera fiable.

Para suprimir esta advertencia al depurar un escenario legítimo, siga estos pasos:

1. Cierre Visual Studio.

1. Establezca el valor de la clave del Registro `DisableAttachSecurityWarning` en 1.

   Busque o cree la clave en `HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger` y, después, establézcala en 1.

   A partir de Visual Studio 2017, si quiere ver toda la configuración del Registro, tendrá que cargar el subárbol del Registro privado. Para más información, vea [How to examine Visual Studio 2017 registry](https://github.com/microsoft/VSProjectSystem/blob/master/doc/overview/examine_registry.md) (Cómo examinar el Registro de Visual Studio 2017). Debe descargar el subárbol del Registro privado antes de iniciar Visual Studio.

1. Reinicie Visual Studio.

1. Cuando termine de depurar el escenario, restablezca el valor a 0, y reinicie Visual Studio.

Entre los "usuarios de confianza" se encuentra usted, además de un conjunto de usuarios estándar que normalmente se definen en equipos que tienen instalado .NET Framework, como es el caso de `aspnet`, `localsystem`, `networkservice` y `localservice`.

## <a name="uielement-list"></a>Lista de UIElement

 Nombre: nombre del ensamblado que se solicitó depurar

 Usuario: usuario actual

 Adjuntar: presione este botón para seguir depurando mediante asociación

 No adjuntar: no se asocia al proceso

## <a name="see-also"></a>Vea también
- [Asociar a procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Seguridad del depurador](../debugger/debugger-security.md)
