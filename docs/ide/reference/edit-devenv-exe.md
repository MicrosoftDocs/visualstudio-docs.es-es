---
title: "/Edit (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "/Edit (modificador para Devenv)"
  - "Devenv, /edit (modificador)"
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Edit (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Abre el archivo especificado en una instancia existente de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Sintaxis  
  
```  
Devenv /edit [file1[ file2]]  
```  
  
## Argumentos  
 `file1`  
 Opcional.  El archivo que se abre en una instancia existente de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Si no existe ninguna instancia de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], se crea una nueva con un diseño de ventanas simplificado y se abre `file1` en la nueva instancia.  
  
 `file2`  
 Opcional.  Uno o varios archivos adicionales que se abren en la instancia existente de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Comentarios  
 Si no se especifica un archivo y existe una instancia de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], la instancia existente de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] recibe el foco.  Si no se especifica un archivo y no existe ninguna instancia de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], se crea una instancia nueva de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] con un diseño de ventanas simplificado.  
  
 Si la instancia existente de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] está en un estado modal, por ejemplo, si el cuadro de diálogo [Opciones](../../ide/reference/options-dialog-box-visual-studio.md) está abierto, el archivo se abrirá en la instancia existente cuando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] salga del estado modal.  
  
## Ejemplo  
 Este ejemplo abre el archivo `MyFile.cs` en una instancia existente de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] o abre el archivo en una nueva instancia de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] si aún no existe una.  
  
```  
devenv /edit MyFile.cs  
```  
  
## Vea también  
 [Modificadores de línea de comandos para Devenv](../../ide/reference/devenv-command-line-switches.md)