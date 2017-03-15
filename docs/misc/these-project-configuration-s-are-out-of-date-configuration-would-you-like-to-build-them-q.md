---
title: "Estas configuraciones de proyecto no est&#225;n actualizadas: &lt;configuration&gt;. &#191;Desea compilarlos? | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.Message.BuildOutOfDateProjects"
ms.assetid: d0711f3b-3a2e-4247-afad-9e6468f9df96
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Estas configuraciones de proyecto no est&#225;n actualizadas: &lt;configuration&gt;. &#191;Desea compilarlos?
Está editando un proyecto de Visual Studio o ha seleccionado un proyecto en el Explorador de soluciones y ha elegido iniciar \(F5\) el proyecto o iniciar sin depurar \(CTRL\+F5\). Uno o varios proyectos permiten depurar sin recompilar, incluso si el proyecto se modificó tras la última compilación.  
  
 El entorno de desarrollo integrado \(IDE\) pregunta si recompilar o no proyectos que permiten depurar sin recompilar.  
  
### Para responder a este mensaje  
  
-   Seleccione uno de los botones de la parte inferior del mensaje. Las opciones son:  
  
|Término|Definición|  
|-------------|----------------|  
|**Sí**|Se recompilarán los proyectos no actualizados. Esto significa que:<br /><br /> -   Si el proyecto aún no se ha compilado, lo hará ahora.<br />-   Si el proyecto se modificó desde la última compilación, se recompila.<br />-   El proyecto se depura o se inicia sin depurar.|  
|**No**|Solo se recompilarán aquellos proyectos no actualizados que deban recompilarse antes de depurarse. Esto significa que:<br /><br /> -   Si el proyecto permite depurar sin recompilar \(por ejemplo, un proyecto de aplicación MFC de Visual C\+\+\), el proyecto no se recompila.<br />-   Si el proyecto se debe recompilar antes de depurarse \(por ejemplo, un proyecto de Visual Basic\), el proyecto se recompila.<br />-   El proyecto se depura o se inicia sin depurar.|  
|**Cancelar**|La operación actual se detiene. No se crea, inicia o depura ningún proyecto.|  
  
## Vea también  
 [Cuadro de diálogo Administrador de configuración](http://msdn.microsoft.com/es-es/fa182dca-282e-4ae5-bf37-e155344ca18b)   
 [Cómo: Crear configuraciones de compilación de soluciones y proyectos](../Topic/How%20to:%20Create%20Solution%20and%20Project%20Build%20Configurations.md)   
 [Cómo: Crear y quitar dependencias del proyecto](../ide/how-to-create-and-remove-project-dependencies.md)   
 [Project Dependencies Dialog Box](http://msdn.microsoft.com/es-es/d66e48c3-3722-40dd-99b4-53d93cac128e)   
 [Project Dependencies, Common Properties, Solution Property Pages Dialog Box](http://msdn.microsoft.com/es-es/2ba638fc-719c-4a79-b166-3455a4374e31)   
 [Compilar aplicaciones en Visual Studio](../ide/compiling-and-building-in-visual-studio.md)   
 [Descripción de las configuraciones de compilación](../ide/understanding-build-configurations.md)   
 [NIB: proyectos como contenedores](http://msdn.microsoft.com/es-es/87d40f63-f487-4767-8963-64beec27ba1b)   
 [NIB: administración elementos en proyectos](http://msdn.microsoft.com/es-es/762e606b-7f44-4b66-97a1-e30a703654a0)