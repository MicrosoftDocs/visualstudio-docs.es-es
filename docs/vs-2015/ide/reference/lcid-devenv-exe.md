---
title: -LCID (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- language default
- locale IDs, setting for IDE
- Devenv, /LCID switch
- locale IDs
- /l Devenv switch
- LCID devenv switch
- /lcid Devenv switch
ms.assetid: 3a3f4e70-ea66-4351-9d62-acb1dec30e8e
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: def8ce2a40e068c602b0182b4580f5e3b524d222
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54782228"
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Establece el idioma predeterminado que se usa para texto, moneda y otros valores en el entorno de desarrollo integrado (IDE).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
devenv {/LCID|/l} LocaleID  
```  
  
## <a name="arguments"></a>Argumentos  
 `LocaleID`  
 Obligatorio. LCID (identificador de configuración regional) del idioma especificado.  
  
## <a name="remarks"></a>Comentarios  
 Carga el IDE y establece el idioma natural predeterminado para el entorno. Este cambio se conserva entre sesiones y se refleja en el panel **Configuración internacional** de las opciones de **Entorno** en el cuadro de diálogo **Opciones** del IDE.  
  
 Si el idioma especificado no está disponible en el sistema del usuario, se omite el modificador /LCID.  
  
 En la tabla siguiente se indican los LCID de los idiomas que admite [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
|Lenguaje|LCID|  
|--------------|----------|  
|Chino (simplificado)|2052|  
|Chino (tradicional)|1028|  
|Inglés|3082|  
|Francés|1036|  
|Alemán|1031|  
|Italiano|1040|  
|Japonés|1041|  
|Coreano|1042|  
|Español|3082|  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo se carga el IDE con cadenas de recursos en inglés.  
  
```  
devenv /LCID 1033  
```  
  
## <a name="see-also"></a>Vea también  
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [Configuración internacional, Entorno, Opciones (Cuadro de diálogo)](../../ide/reference/international-settings-environment-options-dialog-box.md)   
 [Personalizar los diseños de ventana](../../ide/customizing-window-layouts-in-visual-studio.md)
