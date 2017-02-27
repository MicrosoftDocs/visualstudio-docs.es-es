---
title: "C&#243;mo: Limitar la instrumentaci&#243;n a funciones espec&#237;ficas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "herramientas de rendimiento, limitación de la instrumentación a las funciones"
ms.assetid: bd98d6bf-2560-4eba-b063-2facb09f87c4
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# C&#243;mo: Limitar la instrumentaci&#243;n a funciones espec&#237;ficas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede limitar la instrumentación y la recolección de datos a una o más funciones; para ello, deberá establecer determinadas opciones en la página **Avanzadas** de la **Sesión de rendimiento** o en las páginas de propiedades del binario de destino:  
  
-   Si especifica las funciones en la página de propiedades de la sesión de rendimiento, sólo se instrumentan esas funciones en todos los binarios instrumentados de la sesión.  
  
-   Si especifica las funciones en la página de propiedades de un binario de destino, se instrumentan sólo las funciones que estén en ese binario determinado.  Las funciones en otros binarios del rendimiento se instrumentan de la forma habitual.  
  
 La limitación de la recolección de datos de esta forma sólo se admite cuando se selecciona el método de generación de perfiles de instrumentación.  
  
> [!NOTE]
>  También puede utilizar la página **Avanzadas** de las páginas de propiedades de **Sesión de rendimiento** con el fin de establecer otras opciones disponibles para la herramienta de instrumentación de la línea de comandos [VSInstr](../profiling/vsinstr.md) de las herramientas de generación de perfiles.  
  
### Para limitar la instrumentación a funciones específicas de una sesión de rendimiento  
  
1.  En el **Explorador de rendimiento**, haga clic con el botón secundario del mouse en el nombre de la sesión y, a continuación, haga clic en **Propiedades**.  
  
     Aparece el cuadro de diálogo **Páginas de propiedades**.  
  
2.  En el cuadro de diálogo **Páginas de propiedades**, haga clic en **Avanzadas**.  
  
3.  En el cuadro de texto **Opciones de instrumentación adicionales**, utilice la siguiente sintaxis para escribir el nombre de las funciones que desea instrumentar:  
  
     **\/include:** `FuncSpec` **\[;** `FuncSpec` **\]** `...`  
  
     `FuncSpec` es el espacio de nombres y el nombre de la función.  Tiene el formato `Namespace`**::**`FunctionName`.  Utilice punto y coma para separar varias funciones.  Utilice un asterisco \(\*\) para especificar un carácter comodín para uno o más caracteres.  Por ejemplo, **\/include:MyNS::\*** especifica todas las funciones del espacio de nombres MyNS.  
  
    > [!NOTE]
    >  Para enumerar las funciones de un binario, abra una ventana del símbolo del sistema en el directorio de instalación de las herramientas de generación de perfiles \(normalmente el directorio \\Team Tools\\Performance Tools, en el directorio de instalación de [!INCLUDE[vsprvsts](../code-quality/includes/vsprvsts_md.md)]\) y, a continuación, escriba vsinstr \/DumpFuncs.  
  
### Para limitar la instrumentación a funciones específicas de un binario  
  
1.  En el **Explorador de rendimiento**, busque el nombre del binario en el nodo **Destinos** de la sesión de rendimiento.  
  
2.  Haga clic con el botón secundario del mouse en el nombre del binario y seleccione **Propiedades**.  
  
     Aparece el cuadro de diálogo **Páginas de propiedades**.  
  
3.  En el cuadro de diálogo **Páginas de propiedades**, haga clic en **Avanzadas**.  
  
4.  En el cuadro de texto **Opciones de instrumentación adicionales**, utilice la siguiente sintaxis para escribir el nombre de las funciones que desea instrumentar:  
  
     **\/include:** `FuncSpec` **\[;** `FuncSpec` **\]** `...`  
  
     `FuncSpec` es el espacio de nombres y el nombre de la función.  Tiene el formato `Namespace`**::**`FunctionName`.  Utilice punto y coma para separar varias funciones.  Utilice un asterisco \(\*\) para especificar un carácter comodín para uno o más caracteres.  Por ejemplo, **\/include:MyNS::\*** especifica todas las funciones del espacio de nombres MyNS.  
  
    > [!NOTE]
    >  Para enumerar las funciones de un binario, abra una ventana del símbolo del sistema en el directorio de instalación de las herramientas de generación de perfiles \(normalmente el directorio \\Team Tools\\Performance Tools, en el directorio de instalación de [!INCLUDE[vsprvsts](../code-quality/includes/vsprvsts_md.md)]\) y, a continuación, escriba vsinstr \/DumpFuncs.  
  
## Vea también  
 [Controlar la recolección de datos](../profiling/controlling-data-collection.md)   
 [Cómo: Limitar la instrumentación a archivos DLL específicos](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)   
 [Cómo: Especificar opciones de instrumentación adicional](../Topic/How%20to:%20Specify%20Additional%20Instrumentation%20Options.md)