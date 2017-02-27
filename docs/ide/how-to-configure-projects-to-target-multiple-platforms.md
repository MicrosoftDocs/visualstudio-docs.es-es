---
title: "C&#243;mo: Configurar proyectos para m&#250;ltiples plataformas de destino | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "plataformas, cambiar plataformas de destino"
  - "proyectos [Visual Studio], plataformas de destino"
ms.assetid: affa2392-7aed-45ac-9ffa-1d8e0496d590
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# C&#243;mo: Configurar proyectos para m&#250;ltiples plataformas de destino
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proporciona la manera de que una solución se destine a varias plataformas o arquitecturas de CPU diferentes a la vez.  Las propiedades para establecer estas se tiene acceso a través del cuadro de diálogo de **Administrador de configuración** .  
  
## Establecer el destino de una plataforma  
 El cuadro de diálogo **Administrador de configuración** le permite crear y establecer configuraciones y plataformas en nivel de la solución y en nivel del proyecto.  Cada combinación de configuraciones y destinos en el nivel de la solución solo puede tener un único conjunto de propiedades asociado, lo cual le permite cambiar fácilmente entre, por ejemplo, una configuración de lanzamiento destinada a una plataforma [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)], una configuración de lanzamiento destinada a una plataforma x86 y una configuración de depuración destinada a una plataforma x86.  
  
#### Para definir la configuración de modo que esté destinada a un plataforma diferente  
  
1.  En el menú **Compilar**, haga clic en **Administrador de configuración**.  
  
2.  En el **Cuadro de plataforma de soluciones activas**, seleccione la plataforma a la que desee que esté destinada su solución o seleccione **\<Nueva\>** para crear una nueva plataforma.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] compilará la aplicación al destino la plataforma que se establece como la plataforma activa en el cuadro de diálogo de **Administrador de configuración** .  
  
## Quitar una plataforma  
 Si entiende que no necesita una plataforma, puede quitarla utilizando el cuadro de diálogo Administrador de configuración.  Esto quitará toda la configuración de la solución y del proyecto que estableció para dicha combinación de configuración y destino.  
  
#### Para quitar una plataforma  
  
1.  En el menú **Compilar**, haga clic en **Administrador de configuración**.  
  
2.  En el **Cuadro de plataforma de soluciones activas**, seleccione **\<Editar\>**.  Se abrirá el cuadro de diálogo **Editar plataformas de solución**.  
  
3.  Haga clic en la plataforma que desee quitar y haga clic en **Quitar**.  
  
## Establecer una solución como el destino de varias plataformas  
 Como puede cambiar la configuración basándose en la combinación de parámetros de configuración y de plataforma, puede establecer una solución que esté destinada a más de una plataforma.  
  
#### Para establecer el destino de varias plataformas  
  
1.  Utilice el **Administrador de configuración** para agregar al menos dos plataformas de destino para la solución.  
  
2.  Seleccione la plataforma que desee establecer como destino en la lista **Plataforma de soluciones activas**.  
  
3.  Compile la solución.  
  
#### Para compilar varias configuraciones de solución a la vez  
  
1.  Utilice el **Administrador de configuración** para agregar al menos dos plataformas de destino para la solución.  
  
2.  Utilice la ventana **Compilación por lotes** para compilar varias configuraciones de solución a la vez.  
  
 Es posible tener una plataforma en el nivel de la solución establecida en, por ejemplo, [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)], y no tener ningún proyecto dentro de dicha solución que esté destinado a la misma plataforma.  También es posible tener varios proyectos en la solución, cada uno destinado a plataformas diferentes.  Si tiene una de estas situaciones, es conveniente crear una nueva configuración con un nombre descriptivo para evitar confusiones.  
  
## Vea también  
 [Cómo: Crear y editar configuraciones](../ide/how-to-create-and-edit-configurations.md)   
 [Descripción de las configuraciones de compilación](../ide/understanding-build-configurations.md)   
 [Compilar y limpiar proyectos y soluciones en Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)