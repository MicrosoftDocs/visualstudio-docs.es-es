---
title: "Interfaz de asistente (IDTWizard) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDTWizard (interfaz)"
  - "asistentes, interfaz"
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# Interfaz de asistente (IDTWizard)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

El entorno de \(IDE\) desarrollo integrado \(IDE\) utiliza la interfaz de <xref:EnvDTE.IDTWizard> para comunicarse con los asistentes.  Los asistentes deben implementar esta interfaz para su instalación en el IDE.  
  
 el método de <xref:EnvDTE.IDTWizard.Execute%2A> es el único método asociado con la interfaz de <xref:EnvDTE.IDTWizard> .  Los asistentes implementan este método y el IDE llama al método en la interfaz.  El ejemplo siguiente se muestra la firma del método.  
  
```  
/* IDTWizard Method */  
STDMETHOD(Execute)(THIS_  
   /* [in] */ IDispatch *Application,  
   /* [in] */ long hwndOwner,  
   /* [in] */ SAFEARRAY * *ContextParams,  
   /* [in] */ SAFEARRAY * *CustomParams,  
   /* [out] [in] */ wizardResult *RetVal  
   );  
```  
  
 El mecanismo de inicio es similar para los asistentes de **Nuevo proyecto** y de **Agregar nuevo elemento** .  Para iniciar cualquiera, se llama a la interfaz de <xref:EnvDTE.IDTWizard> definido en Dteinternal.h.  La única diferencia es el conjunto de contexto y parámetros personalizados que se pasan a la interfaz cuando se llama a la interfaz.  
  
 La siguiente información describe la interfaz de <xref:EnvDTE.IDTWizard> que los asistentes deben implementar para trabajar en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el IDE.  El IDE llama al método de <xref:EnvDTE.IDTWizard.Execute%2A> en el asistente, pasándole el siguiente:  
  
-   El objeto DTE  
  
     El objeto DTE es la raíz del modelo de automatización.  
  
-   El identificador al cuadro de diálogo de la ventana como se muestra en el segmento de código, `hwndOwner ([in] long)`.  
  
     El asistente utiliza este `hwndOwner` como elemento primario para el cuadro de diálogo del asistente.  
  
-   Parámetros de contexto pasados a la interfaz como variante para SAFEARRAY como se muestra en el segmento de código, `[in] SAFEARRAY (VARIANT)* ContextParams`.  
  
     Los parámetros de contexto contienen una matriz de valores que son específicos del tipo de asistente que se inicia y el estado actual del proyecto.  El IDE pasa los parámetros de contexto el asistente.  Para obtener más información, vea [Parámetros de contexto](../../extensibility/internals/context-parameters.md).  
  
-   Parámetros personalizados pasados a la interfaz como variante para SAFEARRAY como se muestra en el segmento de código, `[in] SAFEARRAY (VARIANT)* CustomParams`.  
  
     Los parámetros personalizados contienen una matriz de parámetros definidos por el usuario.  Un archivo .vsz pasa parámetros personalizados al IDE.  Los valores vienen determinados por las instrucciones de `Param=` .  Para obtener más información, vea [Parámetros personalizados](../../extensibility/internals/custom-parameters.md).  
  
-   los valores devueltos para la interfaz son  
  
    ```  
    wizardResultSuccess = -1,  
    wizardResultFailure = 0  
    wizardResultCancel = 1  
    wizardResultBackout = 2  
    ```  
  
## Vea también  
 [Parámetros de contexto](../../extensibility/internals/context-parameters.md)   
 [Parámetros personalizados](../../extensibility/internals/custom-parameters.md)   
 [Asistentes](../../extensibility/internals/wizards.md)   
 [Asistente \(. Archivo vsz\)](../../extensibility/internals/wizard-dot-vsz-file.md)