---
title: Limitaciones sobre la depuración de WCF | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, debugging limitations
ms.assetid: 8e0333c4-1ddc-4abe-8f1c-d19bf6a2a07a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7696afd789753b85facf44dfeadf1f3f30c1596b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="limitations-on-wcf-debugging"></a>Limitaciones de la depuración de WCF
Hay tres maneras mediante las que puede empezar a depurar un servicio WCF:  
  
-   Se depura un proceso cliente que llama a un servicio. El depurador va al servicio. El servicio no tiene que estar en la misma solución que la aplicación cliente.  
  
-   Se depura un proceso cliente que realiza una solicitud a un servicio. El servicio debe formar parte de la solución.  
  
-   Usa **adjuntar al proceso** para adjuntar a un servicio que se está ejecutando actualmente. La depuración comienza dentro del servicio.  
  
 En este tema se describen las limitaciones de estos escenarios.  
  
## <a name="limitations-on-stepping-into-a-service"></a>Limitaciones de ir a un servicio  
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
  
     Este código solo se tiene que agregar una vez. Puede agregar este código modificando el archivo .config o asociándose al servicio mediante **adjuntar al proceso**. Cuando usas **adjuntar al proceso** en un servicio, el código de depuración se agrega automáticamente al archivo .config. Después de esto, puede depurar e ir al servicio sin tener que modificar el archivo .config.  
  
## <a name="limitations-on-stepping-out-of-a-service"></a>Limitaciones de salir de un servicio  
 Salir de un servicio y regresar al cliente tiene las mismas limitaciones que se describieron para ir a un servicio. Además, el depurador debe estar asociado al cliente. Si está depurando un cliente y va a un servicio, el depurador seguirá asociado al servicio. Esto es cierto si inició el cliente mediante el uso de **Iniciar depuración** o asociado al cliente mediante el uso de **adjuntar al proceso**. Si empieza a depurar asociándose al servicio, el depurador no estará asociado aún al cliente. En ese caso, si tiene que salir del servicio y al cliente, primero debe usar **adjuntar al proceso** para asociar manualmente al cliente.  
  
## <a name="limitations-on-automatic-attach-to-a-service"></a>Limitaciones de la asociación automática a un servicio  
 Asociarse automáticamente a un servicio tiene las siguientes limitaciones:  
  
-   El servicio debe formar parte de la solución de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que está depurando.  
  
-   El servicio debe estar hospedado. Puede formar parte de un proyecto de sitio web (sistema de archivos y HTTP), proyecto de aplicación web (sistema de archivos y HTTP) o proyecto de biblioteca de servicio WCF. Los proyectos de biblioteca de servicio WCF pueden ser bibliotecas de servicio o bibliotecas de servicio de flujo de trabajo.  
  
-   Este servicio se debe invocar desde un cliente WCF.  
  
-   La depuración debe estar habilitada con el siguiente código en el archivo app.config o Web.config:  
  
    ```  
    <system.web>  
      <compilation debug="true" />  
    <system.web>  
    ```  
  
## <a name="self-hosting"></a>Autohospedaje  
 A *hospeda a sí mismo servicio* es un servicio WCF que no se ejecuta dentro de IIS, el Host de servicio WCF o el [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] servidor de desarrollo. Para obtener información acerca de cómo depurar un servicio hospedado por sí mismo, consulte [Cómo: depurar un servicio de WCF Auto-hospedados](../debugger/how-to-debug-a-self-hosted-wcf-service.md).  
  
## <a name="self-hosting"></a>Autohospedaje  
 Para habilitar la depuración de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplicaciones 3.0 o 3.5, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0 o 3.5 debe instalarse antes de [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] está instalado. Si [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] está instalado antes de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0 o 3.5, se produce un error cuando se intenta depurar un [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplicación 3.0 o 3.5. El mensaje de error es, "No se puede ir automáticamente al servidor". Para solucionar este problema, utilice las ventanas **el Panel de Control** > **programas y características** para reparar el [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] instalación.  
  
## <a name="see-also"></a>Vea también  
 [Depurar servicios WCF](../debugger/debugging-wcf-services.md)   
 [Cómo: Depurar un servicio WCF independiente](../debugger/how-to-debug-a-self-hosted-wcf-service.md)