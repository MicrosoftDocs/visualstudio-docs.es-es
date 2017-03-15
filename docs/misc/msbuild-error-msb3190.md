---
title: "Error de MSBuild MSB3190 | Microsoft Docs"
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
  - "GenerateManifest.InvalidRequestedExecutionLevel"
helpviewer_keywords: 
  - "MSB3190"
ms.assetid: 45b45688-9345-45db-adc8-3e200f1c17eb
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3190
**MSB3190: ClickOnce no admite el nivel de ejecución solicitado '\<nivel\>'.**  
  
 Este error se genera en equipos que ejecutan Windows Vista cuando el manifiesto para Control de cuentas de usuario \(UAC\) incrustado de la aplicación especifica que una aplicación ClickOnce debe ejecutarse con credenciales administrativas.  ClickOnce y COM sin registro necesitan un manifiesto externo que especifique que la aplicación se ejecutará como usuario actual.  
  
 ClickOnce no acepta los niveles de ejecución `requireAdministrator` o `highestAvailable`.  Si especifica uno de estos niveles, recibirá este error.  ClickOnce necesita `asInvoker`, pero tampoco aceptará ningún nodo `<requestedExecutionLevel>`, que especifica la virtualización de archivos y del Registro \(significa que no se genera ningún manifiesto; esto se realiza a efectos de compatibilidad con versiones anteriores\).  
  
> [!NOTE]
>  Es posible que su equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones.  La edición de Visual Studio que tenga y la configuración que esté usando determinan estos elementos.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Para corregir este error  
  
-   Genere un manifiesto de UAC externo \(app.manifest\) que especifique que la aplicación se ejecutará como usuario actual \(`asInvoker`\).  
  
     En proyectos de Visual C\#, vaya a la página **Aplicación** del Diseñador de proyectos y haga clic en **Properties\\app.manifest** en la lista **Manifiesto**.  Para obtener más información, vea [Página de aplicación, Diseñador de proyectos \(C\#\)](../ide/reference/application-page-project-designer-csharp.md).  
  
     En proyectos de Visual Basic, vaya a la página **Aplicación** del Diseñador de proyectos y haga clic en el botón **Ver configuración de UAC**.  Se abre app.manifest para su edición.  Edite la siguiente etiqueta del manifiesto para que quede de la siguiente manera:  
  
    ```  
    <requestedExecutionLevel level="asInvoker" />  
    ```  
  
     Para obtener más información, vea [Aplicación \(Página, Diseñador de proyectos\) \(Visual Basic\)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
-   Para obtener más información sobre cómo generar un manifiesto de UAC y especificar el nivel de ejecución, vea [Implementación de ClickOnce en Windows Vista](../deployment/clickonce-deployment-on-windows-vista.md).  
  
## Vea también  
 [Página de aplicación, Diseñador de proyectos \(C\#\)](../ide/reference/application-page-project-designer-csharp.md)   
 [Aplicación \(Página, Diseñador de proyectos\) \(Visual Basic\)](../ide/reference/application-page-project-designer-visual-basic.md)   
 [Implementación de ClickOnce en Windows Vista](../deployment/clickonce-deployment-on-windows-vista.md)