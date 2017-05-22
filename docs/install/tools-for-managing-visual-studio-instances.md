---
title: Herramientas para detectar y administrar instancias de Visual Studio | Microsoft Docs
description: "{{MARCADOR DE POSICIÓN}}"
ms.date: 04/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 85686707-14C0-4860-9B7A-66485D43D241
author: timsneath
ms.author: tims
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: a6c3aa65a2c0198c856f09f6f16f58bf16945d58
ms.contentlocale: es-es
ms.lasthandoff: 05/09/2017

---
# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>Herramientas para detectar y administrar instancias de Visual Studio

## <a name="detecting-existing-visual-studio-instances"></a>Detección de instancias existentes de Visual Studio
Dispone de varias herramientas que le ayudarán a detectar y administrar las instancias de Visual Studio instaladas en los equipos cliente:

* [VSWhere](https://github.com/microsoft/vswhere): ejecutable de C++ que ayuda a encontrar la ubicación de las herramientas principales de Visual Studio desde una instancia instalada de Visual Studio.
* [VSSetup.PowerShell](https://github.com/microsoft/vssetup.powershell): scripts de PowerShell que usan la API de configuración de la instalación para identificar las instancias instaladas de Visual Studio.
* [VS-Setup-Samples](https://github.com/microsoft/vs-setup-samples): ejemplos de C# y C++ que muestran cómo usar la API de configuración de la instalación para consultar una instalación existente.

Además, la [API de configuración de la instalación](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.setup.configuration.aspx) proporciona interfaces para los desarrolladores que quieran crear sus propias utilidades para interrogar instancias de Visual Studio.

>[!TIP]
>Para más información sobre la instalación de Visual Studio 2017, vea los [artículos del blog de Heath Stewart](https://blogs.msdn.microsoft.com/heaths/tag/vs2017/).


## <a name="editing-the-registry-for-a-visual-studio-instance"></a>Edición del Registro para una instancia de Visual Studio
En Visual Studio de 2017, configuración del Registro se almacena en una ubicación privada, lo que permite varias instancias en paralelo de la misma versión de Visual Studio en la misma máquina.

Como estas entradas no se almacenan en el Registro global, hay instrucciones especiales para usar el Editor del Registro para realizar cambios en su configuración:

1. Si tiene abierta una instancia de Visual Studio 2017, ciérrela.
2. Inicie `regedit.exe`.
3. Seleccione el nodo `HKEY_LOCAL_MACHINE`.
4. En el menú principal de Regedit, seleccione **Archivo -> Cargar subárbol ...** y luego seleccione el archivo de Registro privado, que se encuentra almacenado en la carpeta **AppData\Local**. Por ejemplo:
   ```
   %localappdata%\Microsoft\VisualStudio\<config>\privateregistry.bin
   ```

> [!NOTE]
> `<config>` corresponde a la instancia de Visual Studio que le gustaría examinar.

Se le pedirá que proporcione un nombre de subárbol, que se convertirá en el nombre de su subárbol aislado. Después de haber hecho esto, debería poder examinar el Registro bajo el subárbol aislado que creó.

> [!IMPORTANT]
> Antes de iniciar de nuevo Visual Studio, debe descargar el subárbol aislado que creó. Para ello, seleccione Archivo -> Descargar subárbol desde el menú principal de Regedit. (Si no lo hace, el archivo permanecerá bloqueado y Visual Studio no se podrá iniciar).

