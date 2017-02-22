---
title: "Inicio r&#225;pido, Entorno, Opciones (cuadro de di&#225;logo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Environment.QuickLaunch"
  - "vs.quicklaunch"
helpviewer_keywords: 
  - "buscar IDE"
  - "IDE, buscar"
ms.assetid: 4200f297-d065-4723-9a30-d91ff2e26c9d
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Inicio r&#225;pido, Entorno, Opciones (cuadro de di&#225;logo)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Puede usar **Inicio rápido** para buscar y ejecutar acciones rápidamente para los activos IDE como opciones, plantillas y menús.  No puede usar **Inicio rápido** para buscar símbolos y código.  El cuadro de búsqueda **Inicio rápido** está situado en la esquina superior derecha de la barra de menús y es accesible mediante las teclas Ctrl \+ Q.  Simplemente escriba la cadena de búsqueda en el cuadro.  Para buscar cadenas que contengan @, use «@@».  
  
 **Inicio rápido** está habilitado de forma predeterminada al instalar Visual Studio.  En la barra de menús, puede mostrar u ocultar **Inicio rápido** mediante **Herramientas**, **Opciones**.  Expanda el nodo **Entornos** y, a continuación, elija **Inicio rápido**.  Active o desactive la casilla **Habilitar inicio rápido**.  También puede habilitar o deshabilitar categorías de búsqueda en esta página.  
  
## Lista de categorías  
 Aparecen los resultados de búsqueda de inicio rápido en cuatro categorías: **Usados más recientemente**, **Menús**, **Opciones** y **Documentos abiertos**, junto con el número de elementos de la categoría.  Para desplazarse por los resultados de búsqueda por categoría, pulse las teclas Ctrl \+ Q para mostrar todos los resultados de la categoría.  Después de que aparezca la última categoría, CTRL \+ Q le muestra unos pocos resultados de cada categoría.  Puede usar Ctrl \+ Mayús \+ Q para desplazarse por las categorías en orden inverso.  Para ver todos los resultados de búsqueda en una categoría, elija el nombre de la categoría.  
  
 Puede utilizar los siguientes accesos directos para limitar la búsqueda a las categorías específicas.  
  
|Categoría|Acceso directo|Descripción del acceso directo|  
|---------------|--------------------|------------------------------------|  
|Usados más recientemente|@mru<br /><br /> Por ejemplo,`fuente @mru`|Muestra hasta cinco de los elementos que ha **Usado más recientemente**.|  
|Menús|@menu<br /><br /> Por ejemplo, `fuente @menu`|Limita la búsqueda a los elementos de menú.|  
|Opciones|@opt<br /><br /> Por ejemplo,`fuente @opt`|Limita la búsqueda a la configuración del cuadro de diálogo **Opciones**.|  
|Documentos|@doc<br /><br /> Por ejemplo,`fuente @doc`|Limita la búsqueda a los nombres de archivo y rutas de acceso de documentos abiertos para los criterios de búsqueda, pero no busca el texto dentro de los propios archivos.|  
  
> [!NOTE]
>  Puede cambiar las teclas de método abreviado en la página **General**, **Teclado**, en el cuadro de diálogo **Opciones**.  
  
## Mostrar resultados anteriores  
 De forma predeterminada, el término de búsqueda que especifique no se conserva de una sesión de búsqueda a otra.  La cadena de búsqueda está desactivada si busca un término. Mueva el cursor fuera del área de **Inicio rápido** y, a continuación, retroceda.  Para conservar los resultados de búsqueda, vaya al cuadro de diálogo **Opciones**, seleccione **Inicio rápido** y, a continuación, seleccione la casilla **Mostrar resultados de búsqueda de la búsqueda anterior cuando el Inicio rápido está activado**.  La próxima vez que realice una búsqueda, salga del área de Inicio rápido y retroceda. Inicio rápido conservará el término de búsqueda que se utilizó por última vez y también le mostrará los resultados de búsqueda.  
  
 Para conocer las últimas sugerencias y trucos para usar el **Inicio rápido**, consulte el [Blog de Visual Studio](http://go.microsoft.com/fwlink/?LinkId=236054).  
  
## Vea también  
 [Elementos generales de la interfaz de usuario \(Visual Studio\)](../../ide/reference/general-user-interface-elements-visual-studio.md)   
 [Opciones de entorno \(Cuadro de diálogo\)](../../ide/reference/environment-options-dialog-box.md)