---
title: "Limitaciones de la depuraci&#243;n de WCF | Microsoft Docs"
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
  - "depurar, WCF"
  - "WCF, limitaciones de la depuración"
ms.assetid: 8e0333c4-1ddc-4abe-8f1c-d19bf6a2a07a
caps.latest.revision: 30
caps.handback.revision: 30
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Limitaciones de la depuraci&#243;n de WCF
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Hay tres maneras mediante las que puede empezar a depurar un servicio WCF:  
  
-   Se depura un proceso cliente que llama a un servicio.  El depurador va al servicio.  El servicio no tiene que estar en la misma solución que la aplicación cliente.  
  
-   Se depura un proceso cliente que realiza una solicitud a un servicio.  El servicio debe formar parte de la solución.  
  
-   Se utiliza **Asociar al proceso** para asociarse a un servicio que se está ejecutando actualmente.  La depuración comienza dentro del servicio.  
  
 En este tema se describen las limitaciones de estos escenarios.  
  
## Limitaciones de ir a un servicio  
 Para ir a un servicio desde una aplicación cliente que está depurando, se deben cumplir las siguientes condiciones:  
  
-   El cliente debe llamar al servicio utilizando un objeto de cliente sincrónico.  
  
-   La operación del contrato no puede ser unidireccional.  
  
-   Si el servidor es asincrónico, no se puede ver la pila de llamadas completa mientras se esté ejecutando el código dentro del servicio.  
  
-   La depuración debe estar habilitada con el siguiente código en el archivo app.config o Web.config:  
  
    ```  
    <system.web>  
      <compilation debug="true" />  
    </system.web>  
    ```  
  
     Este código solo se tiene que agregar una vez.  Puede agregar este código modificando el archivo .config o asociándose al servicio mediante **Asociar al proceso**.  Si se utiliza **Asociar al proceso** en un servicio, el código de depuración se agrega automáticamente al archivo .config.  Después de esto, puede depurar e ir al servicio sin tener que modificar el archivo .config.  
  
## Limitaciones de salir de un servicio  
 Salir de un servicio y regresar al cliente tiene las mismas limitaciones que se describieron para ir a un servicio.  Además, el depurador debe estar asociado al cliente.  Si está depurando un cliente y va a un servicio, el depurador seguirá asociado al servicio.  Esto es cierto si inició el cliente utilizando **Iniciar depuración** o se asoció al cliente utilizando **Asociar al proceso**.  Si empieza a depurar asociándose al servicio, el depurador no estará asociado aún al cliente.  En tal caso, si tiene que salir del servicio y regresar al cliente, primero deberá utilizar **Asociar al proceso** para asociarse manualmente al cliente.  
  
## Limitaciones de la asociación automática a un servicio  
 Asociarse automáticamente a un servicio tiene las siguientes limitaciones:  
  
-   El servicio debe formar parte de la solución de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que está depurando.  
  
-   El servicio debe estar hospedado.  Puede formar parte de un proyecto de sitio web \(sistema de archivos y HTTP\), proyecto de aplicación web \(sistema de archivos y HTTP\) o proyecto de biblioteca de servicio WCF.  Los proyectos de biblioteca de servicio WCF pueden ser bibliotecas de servicio o bibliotecas de servicio de flujo de trabajo.  
  
-   Este servicio se debe invocar desde un cliente WCF.  
  
-   La depuración debe estar habilitada con el siguiente código en el archivo app.config o Web.config:  
  
    ```  
    <system.web>  
      <compilation debug="true" />  
    <system.web>  
    ```  
  
## Autohospedaje  
 Un *servicio que se hospeda a sí mismo* es un servicio WCF que no se ejecuta dentro de IIS, el host de servicio WCF o el servidor de desarrollo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Para obtener información sobre cómo depurar un servicio autohospedado, vea [Cómo: Depurar un servicio WCF independiente](../debugger/how-to-debug-a-self-hosted-wcf-service.md).  
  
## Autohospedaje  
 Para permitir la depuración de aplicaciones de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0 o 3.5, se debe instalar [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0 o 3.5 antes de instalar [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)].  Si [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] se instala antes de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0 o 3.5, se produce un error al intentar depurar una aplicación de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0 o 3.5.  El mensaje de error es, "No se puede ir automáticamente al servidor". Utilice el **Panel de control** de Windows, **Programas y características**, para corregir este problema y reparar la instalación de [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)].  
  
## Vea también  
 [Depurar servicios WCF](../debugger/debugging-wcf-services.md)   
 [Cómo: Depurar un servicio WCF independiente](../debugger/how-to-debug-a-self-hosted-wcf-service.md)