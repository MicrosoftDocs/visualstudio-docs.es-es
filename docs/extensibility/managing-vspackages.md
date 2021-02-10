---
title: Administrar VSPackages | Microsoft Docs
description: Obtenga información acerca de cómo administrar VSPackages, para saber cuándo puede utilizar simplemente la administración predeterminada de VSPackage proporcionada por Visual Studio y cómo y cuándo personalizarla.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2b0e3b95ee3c715eb21028b6c156b7a62ea82d41
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943223"
---
# <a name="manage-vspackages"></a>Administración de VSPackages
En la mayoría de los casos no es necesario preocuparse por la administración de VSPackages, ya que las plantillas de proyecto y de elemento registran y cargan el paquete automáticamente. Sin embargo, en algunas circunstancias, puede que tenga que aprender un poco más para administrar el paquete.

## <a name="use-the-experimental-instance"></a>Usar la instancia experimental
 Para obtener más información sobre la instancia experimental, vea [la instancia experimental](../extensibility/the-experimental-instance.md).

## <a name="register-and-unregister-vspackages"></a>Registrar y anular el registro de VSPackages
 Para obtener información sobre cómo registrar y anular el registro de VSPackages y otros tipos de extensión, vea [registrar y anular el registro de VSPackages](../extensibility/registering-and-unregistering-vspackages.md).

## <a name="load-a-vspackage"></a>Carga de un VSPackage
 Los VSPackages se pueden configurar para que se carguen de forma autocarga cuando se activa un GUID de CMDUICONTEXT determinado. Para obtener más información, vea [cargar VSPackages](../extensibility/loading-vspackages.md).

## <a name="use-asyncpackage-to-load-vspackages-in-the-background"></a>Usar AsyncPackage para cargar VSPackages en segundo plano
 La `AsyncPackage` clase habilita la carga de paquetes en un subproceso en segundo plano para mejorar la capacidad de respuesta de la interfaz de usuario en Visual Studio. Para obtener más información, vea [Cómo: usar AsyncPackage para cargar VSPackages en segundo plano](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).

## <a name="rule-based-ui-context-for-extensions"></a>Contexto de la interfaz de usuario basada en reglas para las extensiones
 Los contextos de la interfaz de usuario basados en reglas permiten a los autores de extensiones definir las condiciones precisas en las que se activa un contexto de la interfaz de usuario y se cargan los VSPackages asociados. Para obtener más información, consulte [Cómo: usar el contexto de interfaz de usuario basado en reglas para las extensiones de Visual Studio](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).

## <a name="diagnose-extension-performance"></a>Diagnosticar el rendimiento de la extensión
Las extensiones pueden afectar al rendimiento de la carga de la solución y el inicio. Obtenga información sobre cómo se calcula el impacto de las extensiones de Visual Studio y cómo se puede analizar localmente para probar si una extensión puede mostrarse como una extensión que afecta al rendimiento. Para obtener más información, consulte [Cómo: diagnosticar el rendimiento de la extensión](how-to-diagnose-extension-performance.md).

## <a name="troubleshoot-vspackages"></a>Solucionar problemas de VSPackages
 Descubra las técnicas para solucionar problemas de los VSPackages que no cargan o están experimentando errores: [solución de problemas de VSPackages](../extensibility/troubleshooting-vspackages.md)

## <a name="see-also"></a>Vea también
- [VSPackages](../extensibility/internals/vspackages.md)
