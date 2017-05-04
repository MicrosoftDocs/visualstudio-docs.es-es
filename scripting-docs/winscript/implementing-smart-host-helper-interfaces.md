---
title: "Implementar interfaces Smart Host Helper | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Smart Host Helper (Interfaces), implementar"
ms.assetid: b9c44246-4d4d-469e-91be-00c8f5796fa5
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Implementar interfaces Smart Host Helper
La interfaz de [IDebugDocumentHelper \(Interfaz\)](../winscript/reference/idebugdocumenthelper-interface.md) simplifica en gran medida la tarea de crear un host inteligente para la depuración activa, porque proporciona implementaciones para las interfaces necesarias para hospedar inteligente.  
  
 Para ser un host inteligente mediante `IDebugDocumentHelper`, una aplicación host debe hacer solo tres cosas:  
  
1.  `CoCreate` el administrador de la depuración, y utiliza la interfaz de [IProcessDebugManager \(Interfaz\)](../winscript/reference/iprocessdebugmanager-interface.md) para agregar la aplicación a la lista de aplicaciones depurables.  
  
2.  Cree una aplicación auxiliar de depuración para cada objeto de script, utilizando el método de [IProcessDebugManager::CreateDebugDocumentHelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md) .  Asegúrese de que el nombre del documento, el documento primario, texto, y los bloques de script están definidos.  
  
3.  Implemente la interfaz de [IActiveScriptSiteDebug \(Interfaz\)](../winscript/reference/iactivescriptsitedebug-interface.md) en el objeto que implementa la interfaz de [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) \(que es necesaria para Scripting activo\).  El único método no trivial en delegados de la interfaz de `IActiveScriptSiteDebug` simplemente a la aplicación auxiliar.  
  
 Opcionalmente, el host puede implementar la interfaz de [IDebugDocumentHost \(Interfaz\)](../winscript/reference/idebugdocumenthost-interface.md) si necesita un control adicional sobre la sintaxis color, la creación del contexto del documento, y otra funcionalidad extendida.  
  
 La limitación principal de la aplicación auxiliar host inteligente es que controla los documentos cuyo contenido cambian o encogimiento después de que se hayan agregado \(aunque los documentos pueden expandir\).  Para muchos hosts inteligentes, sin embargo, la funcionalidad que proporciona es exactamente lo que es necesario.  
  
 Las secciones siguientes se explica cada paso con más detalle.  
  
## Cree un objeto application  
 Antes de que la aplicación auxiliar host inteligente puede utilizar, es necesario crear un objeto de [IDebugApplication \(Interfaz\)](../winscript/reference/idebugapplication-interface.md) para representar la aplicación en el depurador.  
  
#### Para crear un objeto application  
  
1.  Cree una instancia del administrador de la depuración utilizando `CoCreateInstance`.  
  
2.  Llamar a [IProcessDebugManager::CreateApplication](../winscript/reference/iprocessdebugmanager-createapplication.md).  
  
3.  Establezca el nombre de la aplicación mediante [IDebugApplication::SetName](../winscript/reference/idebugapplication-setname.md).  
  
4.  Agregue el objeto application a la lista de aplicaciones depurables mediante [IProcessDebugManager::AddApplication](../winscript/reference/iprocessdebugmanager-addapplication.md).  
  
     El siguiente código se describe el proceso, pero no incluye la comprobación de errores u otras técnicas de programación sólidos.  
  
    ```  
    CoCreateInstance(CLSID_ProcessDebugManager, NULL,  
          CLSCTX_INPROC_SERVER | CLSCTX_INPROC_HANDLER  
          | CLSCTX_LOCAL_SERVER,  
    IID_IProcessDebugManager, (void **)&g_ppdm);  
    g_ppdm->CreateApplication(&g_pda);  
    g_pda->SetName(L"My cool application");  
    g_ppdm->AddApplication(g_pda, &g_dwAppCookie);  
    ```  
  
## Mediante IDebugDocumentHelper  
  
#### Para utilizar la aplicación auxiliar \(secuencia mínima de pasos\)  
  
1.  Para cada el documento hospedado, crea una aplicación auxiliar mediante [IProcessDebugManager::CreateDebugDocumentHelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md).  
  
2.  Llame a [IDebugDocumentHelper::Init](../winscript/reference/idebugdocumenthelper-init.md) en la aplicación auxiliar, proporcionando el nombre, los atributos del documento, y así sucesivamente.  
  
3.  Llame a [IDebugDocumentHelper::Attach](../winscript/reference/idebugdocumenthelper-attach.md) con la aplicación auxiliar primario para el documento \(o NULL si el documento es la raíz\) para definir la posición del documento en el árbol y para hacerla visible el depurador.  
  
4.  Llame a [IDebugDocumentHelper::AddDBCSText](../winscript/reference/idebugdocumenthelper-adddbcstext.md) o [IDebugDocumentHelper::AddUnicodeText](../winscript/reference/idebugdocumenthelper-addunicodetext.md) para definir el texto del documento.  \(Se pueden llamar varias veces a si el documento se descarga incrementalmente, como en el caso de un explorador.\)  
  
5.  Llamada [IDebugDocumentHelper::DefineScriptBlock](../winscript/reference/idebugdocumenthelper-definescriptblock.md) para definir los intervalos para cada bloque de script y los motores de scripts asociados.  
  
## Implementar IActiveScriptSiteDebug  
 Para implementar [IActiveScriptSiteDebug::GetDocumentContextFromPosition](../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md), obtenga la aplicación auxiliar correspondiente al sitio determinado, y después obtiene el documento inicial de desplazamiento para el contexto especificado de origen, como sigue:  
  
```  
pddh->GetScriptBlockInfo(dwSourceContext, NULL, &ulStartPos, NULL);  
```  
  
 A continuación, utilizará la aplicación auxiliar para crear un contexto de nuevo documento por dado el carácter de desplazamiento:  
  
```  
pddh->CreateDebugDocumentContext(ulStartPos + uCharacterOffset, cChars, &pddcNew);  
```  
  
 Para implementar [IActiveScriptSiteDebug::GetRootApplicationNode](../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md), basta `IDebugApplication::GetRootNode` \(heredado de [IRemoteDebugApplication::GetRootNode](../winscript/reference/iremotedebugapplication-getrootnode.md)\).  
  
 Para implementar [IDebugDocumentHelper::GetDebugApplicationNode](../winscript/reference/idebugdocumenthelper-getdebugapplicationnode.md), devuelva simplemente `IDebugApplication` que creó inicialmente con el administrador del proceso de depuración.  
  
## La interfaz opcional de IDebugDocumentHost  
 El host puede proporcionar una implementación de [IDebugDocumentHost \(Interfaz\)](../winscript/reference/idebugdocumenthost-interface.md) mediante [IDebugDocumentHelper::SetDebugDocumentHost](../winscript/reference/idebugdocumenthelper-setdebugdocumenthost.md) para proporcionarle control adicional sobre la aplicación auxiliar.  Algunas de las cosas clave que la interfaz host permite hacer:  
  
-   Agregue el texto mediante [IDebugDocumentHelper::AddDeferredText](../winscript/reference/idebugdocumenthelper-adddeferredtext.md) de modo que el host no necesite proporcionar caracteres reales inmediatamente.  Cuando los caracteres son realmente necesarios, la aplicación auxiliar llamará [IDebugDocumentHost::GetDeferredText](../winscript/reference/idebugdocumenthost-getdeferredtext.md) en el host.  
  
-   Reemplace el color predeterminado de sintaxis proporcionado por la aplicación auxiliar.  La aplicación auxiliar llama [IDebugDocumentHost::GetScriptTextAttributes](../winscript/reference/idebugdocumenthost-getscripttextattributes.md) para determinar el color para un intervalo de caracteres, el caer posterior en su implementación predeterminada si el retorno `E_NOTIMPL`host.  
  
-   Proporcione un desconocido que controla para los contextos de documento creados por la aplicación auxiliar implementando [IDebugDocumentHost::OnCreateDocumentContext](../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md).  Esto permite al host invalide la funcionalidad de la implementación predeterminada del contexto del documento.  
  
-   Proporcione un nombre de ruta en el sistema de archivos para el documento.  El uso de Usuario que depura esto para permitir que el usuario modifique y guarde los cambios en el documento.  [IDebugDocumentHost::NotifyChanged](../winscript/reference/idebugdocumenthost-notifychanged.md) se llama para notificar al host después de que se ha guardado el documento.  
  
## Vea también  
 [Información general acerca de la depuración de Active Script](../winscript/active-script-debugging-overview.md)