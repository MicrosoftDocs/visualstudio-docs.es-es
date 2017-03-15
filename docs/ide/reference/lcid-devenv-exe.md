---
title: "/LCID (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "/l (modificador para Devenv)"
  - "/lcid (modificador para Devenv)"
  - "Devenv, /LCID (modificador)"
  - "idioma predeterminado"
  - "LCID (modificador para Devenv)"
  - "identificadores de configuración regional"
  - "identificadores de configuración regional, configuración del IDE"
ms.assetid: 3a3f4e70-ea66-4351-9d62-acb1dec30e8e
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /LCID (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Establece el idioma predeterminado utilizado para texto, moneda y otros valores dentro del entorno de desarrollo integrado \(IDE\).  
  
## Sintaxis  
  
```  
devenv {/LCID|/l} LocaleID  
```  
  
## Argumentos  
 `LocaleID`  
 Obligatorio.  LCID \(identificador de configuración regional\) del idioma especificado.  
  
## Comentarios  
 Carga el IDE y establece el idioma natural predeterminado del entorno.  Este cambio persiste entre sesiones y se refleja en el panel **Configuración internacional** de las opciones **Entorno** del cuadro de diálogo **Opciones** del IDE.  
  
 Si el idioma especificado no está disponible en el sistema del usuario, se omitirá el modificador \/LCID.  
  
 La tabla siguiente muestra los LCID de los idiomas admitidos por [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
|Language|LCID|  
|--------------|----------|  
|Chino \(simplificado\)|2052|  
|Chino \(Tradicional\)|1028|  
|Inglés|1033|  
|Francés|1036|  
|Alemán|1031|  
|Italiano|1040|  
|Japonés|1041|  
|Coreano|1042|  
|Español|3082|  
  
## Ejemplo  
 Este ejemplo carga el IDE con cadenas de recursos en inglés.  
  
```  
devenv /LCID 1033  
```  
  
## Vea también  
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [Configuración internacional, Entorno, Opciones \(Cuadro de diálogo\)](../../ide/reference/international-settings-environment-options-dialog-box.md)   
 [Personalizar los diseños de ventana](../../ide/customizing-window-layouts-in-visual-studio.md)