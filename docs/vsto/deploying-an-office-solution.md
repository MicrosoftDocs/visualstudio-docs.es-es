---
title: "Implementar una soluci&#243;n de Office | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "implementación ClickOnce [desarrollo de Office en Visual Studio], acerca de la implementación de soluciones de ClickOnce"
  - "implementación ClickOnce [desarrollo de Office en Visual Studio], visor de eventos"
  - "implementación ClickOnce [desarrollo de Office en Visual Studio], solucionar problemas"
  - "implementar aplicaciones [desarrollo de Office en Visual Studio], visor de eventos"
  - "implementar aplicaciones [desarrollo de Office en Visual Studio], soluciones de Office (2007 system)"
  - "implementar aplicaciones [desarrollo de Office en Visual Studio], solucionar problemas"
  - "aplicaciones de Office [desarrollo de Office en Visual Studio], implementar soluciones de Office"
  - "desarrollo de Office en Visual Studio, implementar soluciones de Office"
  - "desarrollo de Office en Visual Studio, visor de eventos"
  - "desarrollo de Office en Visual Studio, solucionar problemas"
  - "soluciones de Office [desarrollo de Office en Visual Studio], implementar"
  - "soluciones [desarrollo de Office en Visual Studio], implementar soluciones de Office (2007 system)"
ms.assetid: 4cdf4bc6-72c5-4166-8019-d5fd61281079
caps.latest.revision: 78
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 74
---
# Implementar una soluci&#243;n de Office
  Puede implementar soluciones de Office mediante ClickOnce o Windows Installer.  Si usa ClickOnce, se reducirá el número de pasos que requiere la implementación y actualización de la solución.  Si utiliza Windows Installer, obtendrá control sobre cómo se instala la solución y qué páginas muestra el programa de instalación cuando los usuarios instalan la solución.  
  
## Implementar una solución mediante ClickOnce  
 Al implementar una solución mediante ClickOnce, esta se publica en una ubicación centralizada donde los usuarios pueden instalarla y ejecutarla.  Puede actualizar la solución sin tener que distribuir un nuevo programa de instalación a los usuarios.  Esta opción de implementación es más sencilla, pero no puede mostrar a los usuarios las páginas de instalación personalizadas.  Además, las soluciones se deben instalar varias veces en cualquier equipo que tenga más de un usuario.  Vea [Implementar una solución de Office mediante ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
## Implementar una solución mediante Windows Installer  
 Al implementar una solución mediante Windows Installer, distribuirá un programa de instalación a los usuarios y los usuarios instalarán la solución mediante ese programa.  El programa de instalación puede instalar una solución para todos los usuarios de un equipo a la vez, en lugar de solo para el usuario actual.  También tendrá un poco más de control sobre las opciones que se muestran a los usuarios cuando instalan la solución.  Por ejemplo, puede mostrar un contrato de licencia o permitir que los usuarios instalen componentes específicos de una solución.  Sin embargo, si actualiza la solución, debe distribuir un nuevo programa de instalación.  Vea [Implementar una solución de Office mediante Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
## Vea también  
 [Asegurar las soluciones de Office](../vsto/securing-office-solutions.md)   
 [Implementar una solución de Office mediante ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Implementar una solución de Office mediante Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md)   
 [Solucionar problemas de implementación de las soluciones de Office](../vsto/troubleshooting-office-solution-deployment.md)  
  
  