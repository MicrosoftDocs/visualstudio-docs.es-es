---
title: Administración de componentes | Microsoft Docs
description: Obtenga información sobre cómo administrar componentes de Windows Installer al crear un instalador de VSPackage en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9767af4c30957111526303600f9e8eda815b42f0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057096"
---
# <a name="component-management"></a>Administración de componentes
Las unidades de tareas en el Windows Installer se conocen como componentes Windows Installer (a veces denominados WICs o simplemente componentes). Un GUID identifica cada WIC, que es la unidad básica de instalación y el recuento de referencias para las configuraciones que usan Windows Installer.

 Aunque puede usar varios productos para crear el instalador de VSPackage, en esta explicación se presupone el uso de archivos Windows Installer (*. msi*). Al crear el instalador, debe administrar correctamente la implementación de archivos para que el recuento de referencias correcto se produzca en todo momento. Por lo tanto, las distintas versiones del producto no interfieren ni se dividen entre sí en una combinación de escenarios de instalación y desinstalación.

 En Windows Installer, el recuento de referencias se produce en el nivel de componente. Debe organizar cuidadosamente los recursos (archivos, entradas del registro, etc.) en los componentes de. Hay otros niveles de organización (como módulos, características y productos) que pueden ayudar en diferentes escenarios. Para obtener más información, vea [conceptos básicos de Windows Installer](../../extensibility/internals/windows-installer-basics.md).

## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>Instrucciones de creación de la configuración para la instalación en paralelo

- Cree archivos y claves del registro que se compartan entre las versiones en sus propios componentes.

     Si lo hace, puede consumirlos fácilmente en la versión siguiente. Por ejemplo, escriba las bibliotecas que se registran globalmente, extensiones de archivo, otros elementos registrados en **HKEY_CLASSES_ROOT**, etc.

- Agrupe los componentes compartidos en módulos de combinación independientes.

     Esta estrategia le ayuda a crear correctamente la instalación en paralelo.

- Instale los archivos compartidos y las claves del registro con el mismo Windows Installer componentes en todas las versiones.

     Si usa un componente diferente, se desinstalan los archivos y las entradas del registro cuando se desinstala un VSPackage con versiones, pero todavía hay otro VSPackage instalado.

- No mezcle elementos compartidos y versiones en el mismo componente.

     Si lo hace, no es posible instalar elementos compartidos en una ubicación global y elementos con versión en ubicaciones aisladas.

- No tener claves del registro compartidas que señalen a archivos con versiones.

     Si lo hace, se sobrescribirán las claves compartidas cuando se instale otro VSPackage con versiones. Después de quitar la segunda versión, desaparece el archivo al que señala la tecla.

## <a name="see-also"></a>Consulte también
- [Elegir entre VSPackages compartidos y con control de versiones](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [Escenarios de configuración de VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)
