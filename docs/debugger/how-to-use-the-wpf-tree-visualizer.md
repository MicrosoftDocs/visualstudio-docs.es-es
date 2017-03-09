---
title: "C&#243;mo: Usar el visualizador de &#225;rboles de WPF | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurar, WPF"
  - "WPF, depurar"
ms.assetid: 2a1bf1cd-90f9-4d06-9fb4-1bfc925afef3
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Usar el visualizador de &#225;rboles de WPF
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede usar el visualizador de árboles de WPF para explorar el árbol visual de un objeto de WPF y ver las propiedades de dependencia de WPF para los objetos contenidos en ese árbol.  Para obtener más información sobre los árboles visuales, vea [Árboles en WPF](../Topic/Trees%20in%20WPF.md).  Para obtener más información sobre las propiedades de dependencia, vea [Información general sobre las propiedades de dependencia](../Topic/Dependency%20Properties%20Overview.md).  
  
 Al abrir el visualizador de árboles de WPF, verá dos paneles: el **Árbol visual** a la izquierda y las **Propiedades de** *Name***:***Type* a la derecha.  Al seleccionar cualquier objeto en el panel **Árbol visual**, el panel **Propiedades de** *Name***:***Type* se actualizará automáticamente para mostrar las propiedades de dicho objeto.  
  
### Para abrir el visualizador de árboles de WPF  
  
1.  En una Información sobre datos, una ventana **Inspección**, una ventana **Automático** o una ventana **Variables locales**, junto al nombre de un objeto WPF, haga clic en la flecha adyacente al icono de lupa.  
  
     Se mostrará una lista de visualizadores.  
  
2.  Haga clic en **Visualizador de árboles de WPF**.  
  
### Para buscar en el árbol visual  
  
-   En el panel **Árbol visual**, escriba la cadena que desea buscar en el cuadro **Buscar**.  
  
     El visualizador de árboles de WPF buscará inmediatamente el primer objeto del árbol visual que coincida con la cadena que ha escrito.  Escriba más caracteres si desea buscar una coincidencia más precisa.  
  
    -   Para ir a la siguiente coincidencia dentro del árbol visual, haga clic en **Siguiente**.  
  
    -   Para volver a la coincidencia anterior, haga clic en **Anterior**.  
  
    -   Para borrar el criterio de búsqueda, haga clic en **Borrar**.  
  
### Para buscar en la lista de propiedades  
  
-   En el panel **Propiedades de** *Name***:***Type*, escriba la cadena que desea buscar en el cuadro **Filtro**.  
  
     El visualizador de árboles de WPF buscará inmediatamente las propiedades que coincidan con la cadena que ha escrito; ahora, la lista solo muestra las propiedades que coinciden con la cadena que ha escrito.  Escriba más caracteres si desea buscar una coincidencia más precisa.  
  
    -   Para borrar el criterio de búsqueda, haga clic en **Borrar**.  
  
### Para cerrar el visualizador  
  
-   Haga clic en el icono **Cerrar** situado en la esquina superior derecha del cuadro de diálogo.  
  
## Vea también  
 [Cómo: Utilizar un visualizador](../misc/how-to-use-a-visualizer.md)   
 [Visualizadores](../debugger/create-custom-visualizers-of-data.md)   
 [Árboles en WPF](../Topic/Trees%20in%20WPF.md)   
 [Información general sobre las propiedades de dependencia](../Topic/Dependency%20Properties%20Overview.md)