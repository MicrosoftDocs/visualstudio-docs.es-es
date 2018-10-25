---
title: Limitaciones sobre la depuración de WCF | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 001393a856dc374d92e11ff2d4707346a35aea12
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49887428"
---
# <a name="limitations-on-wcf-debugging"></a>Limitaciones de la depuración de WCF
Hay tres maneras mediante las que puede empezar a depurar un servicio WCF:  
  
- Se depura un proceso cliente que llama a un servicio. El depurador va al servicio. El servicio no tiene que estar en la misma solución que la aplicación cliente.  
  
- Se depura un proceso cliente que realiza una solicitud a un servicio. El servicio debe formar parte de la solución.  
  
- Usa **asociar al proceso** para adjuntar a un servicio que se está ejecutando actualmente. La depuración comienza dentro del servicio.  
  
  En este tema se describen las limitaciones de estos escenarios.  
  
## <a name="limitations-on-stepping-into-a-service"></a>Limitaciones de ir a un servicio  
 Para ir a un servicio desde una aplicación cliente que está depurando, se deben cumplir las siguientes condiciones:  
  
-   El cliente debe llamar al servicio utilizando un objeto de cliente sincrónico.  
  
-   La operación del contrato no puede ser unidireccional.  
  
-   Si el servidor es asincrónico, no se puede ver la pila de llamadas completa mientras se esté ejecutando el código dentro del servicio.  
  
-   La depuración debe estar habilitada con el siguiente código en el archivo app.config o Web.config:  
  
    ```xml
    <system.web>  
      <compilation debug="true" />  
    </system.web>  
    ```  
  
     Este código solo se tiene que agregar una vez. Puede agregar este código, edite el archivo .config o mediante la conexión al servicio mediante el uso de **asociar al proceso**. Cuando usas **asociar al proceso** en un servicio, el código de depuración se agrega automáticamente al archivo .config. Después de esto, puede depurar e ir al servicio sin tener que modificar el archivo .config.  
  
## <a name="limitations-on-stepping-out-of-a-service"></a>Limitaciones de salir de un servicio  
 Salir de un servicio y regresar al cliente tiene las mismas limitaciones que se describieron para ir a un servicio. Además, el depurador debe estar asociado al cliente. Si está depurando un cliente y va a un servicio, el depurador seguirá asociado al servicio. Esto es cierto si inició el cliente mediante el uso de **Iniciar depuración** o asociado al cliente mediante el uso de **asociar al proceso**. Si empieza a depurar asociándose al servicio, el depurador no estará asociado aún al cliente. En ese caso, si tiene que salir del servicio y al cliente, primero debe usar **asociar al proceso** para adjuntar manualmente al cliente.  
  
## <a name="limitations-on-automatic-attach-to-a-service"></a>Limitaciones de la asociación automática a un servicio  
 Asociarse automáticamente a un servicio tiene las siguientes limitaciones:  
  
- El servicio debe formar parte de la solución de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que está depurando.  
  
- El servicio debe estar hospedado. Puede ser parte de un proyecto de sitio Web (sistema de archivos y HTTP), proyecto de aplicación Web (sistema de archivos y HTTP) o proyecto de biblioteca de servicios WCF. Los proyectos de biblioteca de servicio WCF pueden ser bibliotecas de servicio o bibliotecas de servicio de flujo de trabajo.  
  
- Este servicio se debe invocar desde un cliente WCF.  
  
- La depuración debe estar habilitada con el siguiente código en el archivo app.config o Web.config:  
  
  ```xml
  <system.web>  
    <compilation debug="true" />  
  <system.web>  
  ```  
  
## <a name="self-hosting"></a>Autohospedaje  
 Un *autohospedado servicio* es un servicio WCF que no se ejecuta dentro de IIS, el Host de servicio WCF o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] servidor de desarrollo. Para obtener información sobre cómo depurar un servicio autohospedado, vea [Cómo: depurar un servicio de WCF autohospedado](../debugger/how-to-debug-a-self-hosted-wcf-service.md).  
  
## <a name="self-hosting"></a>Autohospedaje  
 Para habilitar la depuración de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplicaciones 3.0 o 3.5, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0 o 3.5 debe instalarse antes de [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] está instalado. Si [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] esté instalado antes de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 3.0 o 3.5, se produce un error al intentar depurar un [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplicación 3.0 o 3.5. El mensaje de error es, "No se puede ir automáticamente al servidor". Para corregir este problema, use el Windows **Panel de Control** > **programas y características** para reparar su [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] instalación.  
  
## <a name="see-also"></a>Vea también  
 [Depurar servicios WCF](../debugger/debugging-wcf-services.md)   
 [Cómo: Depurar un servicio WCF independiente](../debugger/how-to-debug-a-self-hosted-wcf-service.md)
