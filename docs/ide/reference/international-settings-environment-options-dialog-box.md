---
title: Configuración internacional, Entorno, Opciones (Cuadro de diálogo)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.InternationalSettings
- VS.ToolsOptionsPages.Environment.International_Settings
- VS.Environment.International Settings
helpviewer_keywords:
- International Settings dialog box
- languages, environment settings
- Options dialog box, international settings
- languages, specifying default
ms.assetid: e3a8815c-6995-4099-8e88-34f91fad55b2
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1526e1c49636f4883392caa63966714625d066d6
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595519"
---
# <a name="options-dialog-box-environment--international-settings"></a>Cuadro de diálogo Opciones: Entorno \> Configuración internacional

La página Configuración internacional le permite cambiar el idioma predeterminado si tiene más de una versión de idioma del entorno de desarrollo integrado (IDE) instalado en su equipo. Puede acceder a este cuadro de diálogo seleccionando **Opciones** desde el menú **Herramientas** y, después, eligiendo **Configuración internacional** desde la carpeta **Entorno**.

**Idioma**

Muestra los idiomas disponibles para las versiones de idioma del producto instalado. Si varios idiomas de productos o una instalación de idiomas mixta de productos comparten el entorno, la selección del idioma se cambia a **Igual que en Microsoft Windows**.

> [!CAUTION]
> En un sistema con múltiples idiomas instalados, las herramientas de compilación de Visual C++ (cl.exe, link.exe, nmake.exe, bscmake.exe y archivos relacionados) no se ven afectadas por esta configuración. Estas herramientas usan la versión del último idioma instalado. Las herramientas de compilación del idioma instalado previamente se sobrescriben porque las herramientas de compilación de Visual C++ no usan el modelo de archivo DLL satélite.

### <a name="see-also"></a>Vea también

- [Instalar paquetes de idioma](../../install/install-visual-studio.md#step-6---install-language-packs-optional)
