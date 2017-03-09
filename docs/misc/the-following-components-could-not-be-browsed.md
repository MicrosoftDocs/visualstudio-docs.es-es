---
title: "The following components could not be browsed: | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS_E_CANNOTBROWSECOM"
  - "VS.Message.0x00006A6D"
  - "VS_E_LOADTYPELIBFAILED"
  - "VS_E_INVALIDCOMCOMPONENT"
  - "VS_E_UNRECOGNIZEDCOMPONENT"
  - "VS.Message.0x00006A6E"
  - "VS.Message.ObjectBrowserErrors"
  - "vs.Message.0x00005AC3"
  - "VS.Message.0x00005AC4"
  - "VS.Message.0x00005AC5"
  - "VS_E_REGFAILEDCOMCOMPONENT"
ms.assetid: 83b03767-eecb-47a4-8029-166308c7dded
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The following components could not be browsed:
Este cuadro de mensaje puede contener una lista con varios errores relacionados con los el Examinador de objetos y con el cuadro de diálogo Selección de componentes.  Estos son algunos de los errores más comunes.  
  
## El componente o tipo de archivo no se puede ver en el Examinador de objetos.  
 Este error se produce normalmente cuando se especifica un nombre de archivo que no existe o no es válido, o cuando no se puede examinar un archivo con el Examinador de objetos.  
  
#### Para corregir este error  
  
-   Compruebe que existe el nombre de archivo especificado, y que es un componente que puede explorarse, como un ensamblado .NET, una biblioteca de tipos COM o un archivo de explorador de código fuente.  
  
## El archivo no es un componente .NET Frameworks o COM válido.  
 Este error suele ocurrir cuando el componente especificado no es un ensamblaje de .NET Framework o una biblioteca de tipos COM.  
  
#### Para corregir este error  
  
-   Elija un componente diferente para explorar.  
  
## No se puede registrar el archivo como componente COM  
 Este error se produce normalmente cuando la biblioteca de tipos de un componente COM no puede registrarse.  Es posible que la biblioteca de tipos no exista o que esté dañada.  
  
#### Para corregir este error  
  
-   Vuelva a instalar el componente e inténtelo de nuevo.  
  
## No hay ninguna biblioteca de tipos coincidente registrada, o la información registrada no es válida.  
 Es posible que la biblioteca de tipos especificada no exista, o que no contenga información válida.  
  
#### Para corregir este error  
  
-   Compruebe que la biblioteca de tipos existe y está registrada correctamente.  
  
## Faltan los componentes necesarios para explorar bibliotecas de tipos COM, o no están registrados correctamente.  
 Falta el archivo vstlbinf.dll, o está registrado incorrectamente.  
  
#### Para corregir este problema.  
  
1.  Busque vstlbinf.dll en su equipo y regístrelo mediante regsvr32.exe.  
  
     \-O bien\-  
  
2.  Si no encuentra el archivo vstlbinf.dll en su equipo, vuelva a instalar este producto.  
  
## Vea también  
 [Object Browser](http://msdn.microsoft.com/es-es/f89acfc5-1152-413d-9f56-3dc16e3f0470)   
 [Edit Custom Component Set Dialog Box](http://msdn.microsoft.com/es-es/dc995bd7-afbf-4389-ba1c-f377b677ded7)