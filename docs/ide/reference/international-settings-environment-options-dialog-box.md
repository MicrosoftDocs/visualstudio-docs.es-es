---
title: Configuración internacional, Entorno, Opciones (Cuadro de diálogo) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Environment.InternationalSettings
- VS.ToolsOptionsPages.Environment.International_Settings
- VS.Environment.International Settings
- VS.ToolsOptionsPag.Environment.International_Settings
helpviewer_keywords:
- International Settings dialog box
- languages, environment settings
- Options dialog box, international settings
- languages, specifying default
ms.assetid: e3a8815c-6995-4099-8e88-34f91fad55b2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 33e206e4c38b4bde715d72c6b8eb4b5bdf9c5dd8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="international-settings-environment-options-dialog-box"></a>Configuración internacional, Entorno, Opciones (Cuadro de diálogo)
La página Configuración internacional le permite cambiar el idioma predeterminado si tiene más de una versión de idioma del entorno de desarrollo integrado (IDE) instalado en su equipo. Puede acceder a este cuadro de diálogo seleccionando **Opciones** desde el menú **Herramientas** y, después, eligiendo **Configuración internacional** desde la carpeta **Entorno**. Si esta página no aparece en la lista, en el cuadro de diálogo **Opciones**, seleccione **Mostrar todas las configuraciones**.  
  
> [!NOTE]
>  Las opciones disponibles en los cuadros de diálogo, así como los nombres y las ubicaciones de los comandos de menú que se ven, podrían diferir de lo que se describe en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para más información, vea [Personalizar el IDE de Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  
  
 **Idioma**  
 Muestra los idiomas disponibles para las versiones de idioma del producto instalado. Esta opción no está disponible a menos que tenga más de una versión de idioma instalada en su equipo. Si varios idiomas de productos o una instalación de idiomas mixta de productos comparten el entorno, la selección del idioma se cambia a **Igual que en Microsoft Windows**.  
  
> [!CAUTION]
>  En un sistema con múltiples idiomas instalados, las herramientas de compilación de Visual C++ (cl.exe, link.exe, nmake.exe, bscmake.exe y archivos relacionados) no se ven afectadas por esta configuración. Estas herramientas usan la versión del último idioma instalado. Las herramientas de compilación del idioma instalado previamente se sobrescriben porque las herramientas de compilación de Visual C++ no usan el modelo de archivo DLL satélite.  
  
## <a name="see-also"></a>Vea también  
 [Instalar paquetes de idioma](../../install/install-visual-studio.md#step-6---install-language-packs-optional)   
 [Opciones de entorno (Cuadro de diálogo)](../../ide/reference/environment-options-dialog-box.md)