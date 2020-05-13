---
title: Administración de VSPackages ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60745d07679ae53b85d169473ed37ab314b67624
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702649"
---
# <a name="manage-vspackages"></a>Administración de VSPackages
En la mayoría de los casos, no es necesario preocuparse por la administración de VSPackages, ya que las plantillas de proyecto y elemento registran y cargan el paquete automáticamente. Sin embargo, en algunas circunstancias es posible que necesite aprender un poco más para administrar su paquete.

## <a name="use-the-experimental-instance"></a>Utilice la instancia experimental
 Para obtener más información sobre la instancia experimental, consulte [La instancia experimental](../extensibility/the-experimental-instance.md).

## <a name="register-and-unregister-vspackages"></a>Registrar y anular el registro de VSPackages
 Para averiguar cómo registrar y anular el registro de VSPackages y otros tipos de extensión, vea Registrar y anular el registro de [VSPackages](../extensibility/registering-and-unregistering-vspackages.md).

## <a name="load-a-vspackage"></a>Cargar un VSPackage
 VSPackages se pueden establecer en autoload cuando un GUID CMDUICONTEXT determinado está activado. Para obtener más información, vea [Cargar VSPackages](../extensibility/loading-vspackages.md).

## <a name="use-asyncpackage-to-load-vspackages-in-the-background"></a>Use AsyncPackage para cargar VSPackages en segundo plano
 La `AsyncPackage` clase permite la carga de paquetes en un subproceso en segundo plano para una mejor capacidad de respuesta de la interfaz de usuario en Visual Studio. Para obtener más información, vea [Cómo: usar AsyncPackage para cargar VSPackages en segundo plano.](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md)

## <a name="rule-based-ui-context-for-extensions"></a>Contexto de interfaz de usuario basado en reglas para extensiones
 Contextos de interfaz de usuario basados en reglas permite a los autores de extensiones definir las condiciones precisas en las que se activa un contexto de interfaz de usuario y se cargan vsPackages asociados. Para obtener más información, vea Cómo: Usar el contexto de interfaz de [usuario basado en reglas para extensiones](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md)de Visual Studio .

## <a name="diagnose-extension-performance"></a>Diagnosticar el rendimiento de la extensión
Las extensiones pueden afectar al rendimiento de la carga de la solución y el inicio. Obtenga información sobre cómo se calcula el impacto de la extensión de Visual Studio y cómo se puede analizar localmente para probar si una extensión puede mostrarse como una extensión que afecta al rendimiento. Para obtener más información, consulte [Cómo: diagnosticar](how-to-diagnose-extension-performance.md)el rendimiento de la extensión .

## <a name="troubleshoot-vspackages"></a>Solución de problemas de VSPackages
 Descubra las técnicas para solucionar problemas de VSPackages que no se cargan o experimentan errores: [Solucionar problemas de VSPackages](../extensibility/troubleshooting-vspackages.md)

## <a name="see-also"></a>Vea también
- [VSPackages](../extensibility/internals/vspackages.md)
