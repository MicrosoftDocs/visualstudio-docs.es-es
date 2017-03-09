---
title: "El tipo de proyecto no es compatible con esta instalaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.projectflavornotavailable"
ms.assetid: 50e92aff-3ce9-4600-94af-4a16e9dffc90
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# El tipo de proyecto no es compatible con esta instalaci&#243;n
Este error se produce cuando intenta abrir un tipo de proyecto que requiere un kit de desarrollo de software \(SDK\) que no se instala con Visual Studio.  Por ejemplo, este error se produce si se abre Visual Studio en un equipo que no tiene instalado Visual Studio SDK y después de intenta abrir un archivo de proyecto para ese SDK, como un proyecto VSIX. \(Para obtener más información sobre Visual Studio SDK, vea [Extensión de Visual Studio](http://go.microsoft.com/fwlink/?LinkID=64968)\).  
  
## Solución alternativa  
 Debe comprobar que tiene el SDK correcto instalado para el tipo de proyecto que está intentando abrir.  
  
#### Para comprobar si ya tiene instalado el SDK  
  
1.  En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
2.  En el cuadro de diálogo **Nuevo proyecto**, expanda el nodo **Instalado**, expanda el nodo **Plantillas** y, a continuación, elija el nodo **Otros tipos de proyectos**.  
  
3.  Examine los tipos de proyecto disponibles para determinar si el proyecto que está intentando abrir está disponible.  
  
 Si no encuentra el tipo de proyecto que está intentando abrir, no tiene instalado el SDK asociado.  Debe buscar e instalar el SDK asociado para abrir el tipo de proyecto.  
  
## Vea también  
 [Novedades de Visual Studio 2015](../ide/what-s-new-in-visual-studio-2015.md)   
 [Portar, migrar y actualizar proyectos de Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)