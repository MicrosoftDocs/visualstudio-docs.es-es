---
title: "C&#243;mo: Depurar una aplicaci&#243;n ClickOnce con permisos restringidos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depuración [Visual Studio], aplicaciones ClickOnce"
  - "implementación de ClickOnce, depuración"
  - "aplicaciones ClickOnce, depuración"
ms.assetid: 6991ea91-5253-451b-923d-22273a3d38b1
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 10
---
# C&#243;mo: Depurar una aplicaci&#243;n ClickOnce con permisos restringidos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Como desarrollador, probablemente esté ejecutando su equipo de desarrollo con permisos de plena confianza, por lo que no verá las mismas excepciones de seguridad al depurar una aplicación ClickOnce que las que podría ver el usuario final al ejecutarlo con permisos restringidos.  
  
 Para detectar estas excepciones, debe depurar la aplicación con los mismos permisos que el usuario final. Se puede habilitar la depuración con permisos restringidos en la página **Seguridad** del **Diseñador de proyectos**.  
  
 Además, al desarrollar aplicaciones que llaman a servicios web, dichos servicios suelen residir en el equipo de desarrollo. Una vez implementados, el usuario final tendrá acceso a estos servicios desde una dirección URL diferente. Para emular la experiencia del usuario final durante la depuración, puede especificar una dirección URL y el depurador tratará los servicios web como si se llamaran desde esa dirección URL.  
  
### Para habilitar la depuración con permisos restringidos  
  
1.  Seleccione un proyecto en el **Explorador de soluciones** y, en el menú **Proyecto**, haga clic en **Propiedades**.  
  
2.  En el **Diseñador de proyectos**, haga clic en la pestaña **Seguridad**.  
  
3.  Active la casilla **Habilitar configuración de seguridad de ClickOnce** y haga clic en el botón de la opción **Aplicación de confianza parcial**.  
  
4.  Haga clic en el botón **Avanzada**.  
  
5.  Active la casilla **Depurar esta aplicación con el conjunto de permisos seleccionados** y haga clic en **Aceptar**.  
  
     Al depurar la aplicación, si intenta obtener acceso a un permiso que no forma parte del conjunto de permisos, se producirá una excepción de seguridad.  
  
### Para especificar una dirección URL para la depuración  
  
1.  Seleccione un proyecto en el **Explorador de soluciones** y, en el menú **Proyecto**, haga clic en **Propiedades**.  
  
2.  En el **Diseñador de proyectos**, haga clic en la pestaña **Seguridad**.  
  
3.  Active la casilla **Habilitar configuración de seguridad de ClickOnce** y haga clic en el botón de la opción **Aplicación de confianza parcial**.  
  
4.  Haga clic en el botón **Avanzada**.  
  
5.  Active la casilla **Depurar esta aplicación con el conjunto de permisos seleccionados** y haga clic en **Aceptar**.  
  
6.  En el cuadro de texto **Depurar esta aplicación como si se hubiera descargado de la siguiente dirección URL**, indique una dirección URL o una ruta de acceso a la red.  
  
## Vea también  
 [Cómo: Establecer permisos personalizados para una aplicación ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Seguridad de acceso del código para aplicaciones ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)