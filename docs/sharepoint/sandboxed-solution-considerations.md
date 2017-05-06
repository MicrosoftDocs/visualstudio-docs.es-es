---
title: "Consideraciones sobre las soluciones en espacio aislado"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.Project.SandboxedSolutions"
  - "VS.SharePointTools.Security.SandboxedSolutions"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "soluciones de granja de servidores [desarrollo de SharePoint en Visual Studio]"
  - "soluciones en espacio aislado [desarrollo de SharePoint en Visual Studio]"
  - "desarrollo de SharePoint en Visual Studio, soluciones de granja de servidores"
  - "desarrollo de SharePoint en Visual Studio, soluciones en espacio aislado"
ms.assetid: 6c2d2dc6-4acb-4b68-ba94-a61087e8dff0
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Consideraciones sobre las soluciones en espacio aislado
  Las *soluciones en espacio aislado* son una característica de Microsoft SharePoint 2010 que permite a los usuarios de la colección de sitios cargar sus propias soluciones de código personalizadas.  Una solución en espacio aislado normal consiste en que los usuarios cargan sus elementos web.  
  
 Una aplicación de SharePoint en espacio aislado se ejecuta en un proceso supervisado y seguro que tiene acceso a una parte limitada de la granja de servidores web.  Microsoft SharePoint 2010 utiliza una combinación de características, galerías de soluciones, supervisión de soluciones y un marco de validación para habilitar las soluciones en un espacio aislado.  
  
## Especificar el nivel de confianza del proyecto  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] admite las soluciones en espacio aislado a través de una propiedad de proyecto booleana denominada *Sandboxed Solution*.  Esta propiedad se puede establecer en cualquier momento en el proyecto o especificarse cuando se crea el proyecto en el **Asistente para la personalización de SharePoint**.  
  
> [!NOTE]  
>  Si se cambia la propiedad *Sandboxed Solution* de un proyecto una vez creado, se pueden producir errores de validación.  
  
 La solución se considera una solución de granja \- ámbito si la propiedad de *Sandboxed Solution* se establece en **false** o elige la opción de **Implementar como solución de granja de servidores** .  Sin embargo, la solución se trata de manera diferente de una solución de granja si la propiedad de *Sandboxed Solution* se establece en **true** o elige la opción de **Implementar como solución en espacio aislado** en el asistente.  
  
## Jerarquía de los sitios de SharePoint  
 Para entender cómo funcionan las soluciones en espacio aislado, conviene saber que los sitios de SharePoint son jerárquicos en ámbito.  El elemento superior se conoce como Granja de servidores web y los demás elementos se subordinan a él:  
  
 Granja de servidores web  
  
 Aplicación web A  
  
 Colección de sitios A1  
  
 Sitio A1a  
  
 Aplicación web B  
  
 Colección de sitios B1  
  
 Sitio B1a  
  
 Sitio B1b  
  
 Colección de sitios B2  
  
 Sitio B2a  
  
 Como se puede ver, las granjas de servidores web pueden contener una o más aplicaciones web, que a su vez pueden contener una o más colecciones de sitios, que pueden tener subsitios, etc.  Los cambios efectuados en una colección de sitios afectan a esa colección únicamente y a ninguna otra.  Sin embargo, los cambios efectuados en el nivel de la granja de servidores web afectan a todas las colecciones de sitios de la granja.  
  
 Windows SharePoint Services 3.0 \(WSS\) solo permite implementar soluciones en el nivel de granja, pero [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] permite implementar en el nivel de granja \(solución de granja\) o en el nivel de la colección de sitios \(solución en espacio aislado\).  
  
## ¿Por qué soluciones en espacio aislado?  
 En WSS 3.0, las soluciones solo se podían implementar en el nivel de granja.  Esto significaba que era posible implementar soluciones potencialmente dañinas o desestabilizadoras que afectaban a toda la granja de servidores web y a las demás colecciones de sitios y aplicaciones que se ejecutaban bajo ella.  Sin embargo, con las soluciones en espacio aislado, es posible implementar soluciones en una subárea de la granja, en una colección de sitios concreta.  Para proporcionar protección adicional, el ensamblado de la solución no se carga en el proceso principal de [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] \(w3wp.exe\),  sino que se carga en un proceso independiente \(SPUCWorkerProcess.exe\).  Este proceso se supervisa e implementa cuotas y limitaciones de peticiones para proteger la granja de las soluciones en espacio aislado que realizan actividades dañinas, como ejecutar bucles de pequeñas dimensiones que consumen ciclos de la CPU.  
  
## galería de soluciones de colecciones de sitios  
 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 2010 incluye una característica que se conoce como “galería de soluciones de colecciones de sitios”. Puede tener acceso a esta característica de la página Administración central de SharePoint 2010 o abriendo el menú de **Acciones del sitio** , eligiendo **Configuración del sitio**, y después elegir el vínculo de **Soluciones** en  **Galerías** en el sitio de SharePoint.  Las galerías de soluciones son repositorios de soluciones que permiten a los administradores de colecciones de sitios administrar las soluciones de sus colecciones de sitios.  
  
 La galería de soluciones es una biblioteca de documentos almacenada en el web raíz del sitio de SharePoint.  La galería de soluciones reemplaza a las plantillas de sitio y admite paquetes de solución.  Cuando se carga un archivo de paquete de solución de SharePoint \(.wsp\), se procesa como una solución en espacio aislado.  
  
## Limitaciones de las soluciones en espacio aislado  
 Cuando se implementa una solución en un espacio aislado, la matriz de funcionalidad de SharePoint disponible para la solución se limita para ayudar a reducir las posibles vulnerabilidades de seguridad que pueda tener.  Algunas de estas limitaciones se exponen a continuación:  
  
-   Las soluciones en espacio aislado disponen de un subconjunto restringido de elementos de solución implementables.  Las plantillas de proyecto de SharePoint potencialmente vulnerables, como las definiciones y los flujos de trabajo del sitio, no están disponibles.  
  
-   SharePoint ejecuta el código de la solución en espacio aislado en un proceso \(SPUCWorkerProcess.exe\) independiente del proceso del grupo de aplicaciones principal de [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] \(w3wp.exe\).  
  
-   Las carpetas asignadas no se pueden agregar al proyecto.  
  
-   Los tipos del ensamblado Microsoft.Office.Server de [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] no se pueden usar en las soluciones en espacio aislado.  Además, solo se pueden usar los tipos del ensamblado Microsoft.SharePoint de [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] en las soluciones en espacio aislado.  
  
 Es importante tener en cuenta que especificar una solución de SharePoint como solución en espacio aislado no tiene ningún efecto en el servidor de SharePoint; únicamente determina el modo de implementar el proyecto de SharePoint en SharePoint desde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] y a qué ensamblados está enlazado.  No afecta al archivo .wsp generado, y el archivo .wsp no tiene datos directamente correlacionados con la propiedad *Sandboxed Solution*.  
  
## Capacidades y elementos de las soluciones en espacio aislado  
 Las soluciones en espacio aislado admiten las capacidades y elementos siguientes:  
  
-   Tipos\/Campos de contenido  
  
-   Acciones personalizadas  
  
-   Flujos de trabajo declarativos  
  
-   Receptores de eventos  
  
-   Llamadas de característica  
  
-   Definiciones de lista  
  
-   Instancias de lista  
  
-   Módulo\/archivos  
  
-   Navegación  
  
-   Onet.xml  
  
-   SPItemEventReceiver  
  
-   SPListEventReceiver  
  
-   SPWebEventReceiver  
  
-   Compatibilidad con todos los elementos web que derivan de `System.Web.UI.WebControls.WebParts.WebPart`  
  
-   Elementos Web  
  
-   Elementos de la característica WebTemplate \(en lugar de Webtemp.xml\)  
  
-   Elementos web visuales  
  
 Las soluciones en espacio aislado no admiten las capacidades y elementos siguientes:  
  
-   Páginas de aplicación  
  
-   Grupo de acciones personalizadas  
  
-   Características del ámbito de granja  
  
-   Elemento `HideCustomAction`  
  
-   Características del ámbito de aplicación web  
  
-   Flujos de trabajo con código  
  
## Vea también  
 [Diferencias entre soluciones en espacio aislado y soluciones de granja](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  