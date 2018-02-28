---
title: "Implementación de interfaces auxiliares para hosts inteligentes | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Smart Host Helper Interfaces, implementing
ms.assetid: b9c44246-4d4d-469e-91be-00c8f5796fa5
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba571f6ad66855c44902e06467889e2cae5b4555
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="implementing-smart-host-helper-interfaces"></a>Implementación de interfaces auxiliares para hosts inteligentes
La interfaz [IDebugDocumentHelper (interfaz)](../winscript/reference/idebugdocumenthelper-interface.md) simplifica en gran medida la tarea de crear un host inteligente para la depuración activa, ya que ofrece implementaciones de muchas interfaces necesarias para el hospedaje inteligente.  
  
 Para ser un host inteligente con `IDebugDocumentHelper`, una aplicación host solo debe realizar tres cosas:  
  
1.  `CoCreate` el administrador de depuración del proceso y usar la interfaz [IProcessDebugManager (interfaz)](../winscript/reference/iprocessdebugmanager-interface.md) para agregar la aplicación a la lista de aplicaciones depurables.  
  
2.  Cree un´auxiliar de documento de depuración para cada objeto de script mediante el método [IProcessDebugManager::CreateDebugDocumentHelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md). Asegúrese de que el nombre del documento, el documento principal, el texto y los bloques de script estén definidos.  
  
3.  Implemente la interfaz [IActiveScriptSiteDebug (interfaz)](../winscript/reference/iactivescriptsitedebug-interface.md) en el objeto que implementa la interfaz [IActiveScriptSite](../winscript/reference/iactivescriptsite.md), necesaria para Active Scripting. El único método no trivial en la interfaz `IActiveScriptSiteDebug` simplemente se delega al auxiliar.  
  
 De forma opcional, el host puede implementar la interfaz [IDebugDocumentHost (interfaz)](../winscript/reference/idebugdocumenthost-interface.md) si necesita control adicional sobre el color de sintaxis, la creación del contexto de documento y otra funcionalidad extendida.  
  
 La principal limitación del auxiliar de host inteligente es que solo puede controlar documentos cuyo contenido cambie o se reduzca una vez agregados los documentos, aunque pueden expandirse. Sin embargo, en el caso de muchos hosts inteligentes, la funcionalidad que ofrece es exactamente la que se necesita.  
  
 En las secciones siguientes se describe cada paso con mayor detalle.  
  
## <a name="create-an-application-object"></a>Creación de un objeto de aplicación  
 Para poder usar el auxiliar de host inteligente, hay que crear un objeto [IDebugApplication (interfaz)](../winscript/reference/idebugapplication-interface.md) que represente la aplicación en el depurador.  
  
#### <a name="to-create-an-application-object"></a>Para crear un objeto de aplicación  
  
1.  Cree una instancia del administrador de depuración del proceso mediante `CoCreateInstance`.  
  
2.  Llame a [IProcessDebugManager::CreateApplication](../winscript/reference/iprocessdebugmanager-createapplication.md).  
  
3.  Establezca el nombre de la aplicación mediante [IDebugApplication::SetName](../winscript/reference/idebugapplication-setname.md).  
  
4.  Agregue el objeto de aplicación a la lista de aplicaciones depurables mediante [IProcessDebugManager::AddApplication](../winscript/reference/iprocessdebugmanager-addapplication.md).  
  
     El código siguiente describe el proceso, pero no incluye la comprobación de errores ni otras técnicas de programación sólida.  
  
    ```  
    CoCreateInstance(CLSID_ProcessDebugManager, NULL,  
          CLSCTX_INPROC_SERVER | CLSCTX_INPROC_HANDLER  
          | CLSCTX_LOCAL_SERVER,  
    IID_IProcessDebugManager, (void **)&g_ppdm);  
    g_ppdm->CreateApplication(&g_pda);  
    g_pda->SetName(L"My cool application");  
    g_ppdm->AddApplication(g_pda, &g_dwAppCookie);  
    ```  
  
## <a name="using-idebugdocumenthelper"></a>Uso de IDebugDocumentHelper  
  
#### <a name="to-use-the-helper-minimal-sequence-of-steps"></a>Para usar el auxiliar (secuencia mínima de pasos)  
  
1.  Para cada documento host, cree un auxiliar mediante [IProcessDebugManager::CreateDebugDocumentHelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md).  
  
2.  Llame a [IDebugDocumentHelper::Init](../winscript/reference/idebugdocumenthelper-init.md) en el auxiliar para obtener el nombre, los atributos del documento, etc.  
  
3.  Llame a [IDebugDocumentHelper::Attach](../winscript/reference/idebugdocumenthelper-attach.md) con el auxiliar principal del documento (o NULL si se trata del documento raíz) para definir la posición del documento en el árbol y hacerlo visible para el depurador.  
  
4.  Llame a [IDebugDocumentHelper::AddDBCSText](../winscript/reference/idebugdocumenthelper-adddbcstext.md) o [IDebugDocumentHelper::AddUnicodeText](../winscript/reference/idebugdocumenthelper-addunicodetext.md) para definir el texto del documento. (Si el documento se descarga de forma incremental, como en el caso de un explorador, puede llamar a estos métodos llamar varias veces).  
  
5.  Llame a [IDebugDocumentHelper::DefineScriptBlock](../winscript/reference/idebugdocumenthelper-definescriptblock.md) para definir los intervalos de cada bloque de script y los motores de script asociados.  
  
## <a name="implementing-iactivescriptsitedebug"></a>Implementación de IActiveScriptSiteDebug  
 Para implementar [IActiveScriptSiteDebug::GetDocumentContextFromPosition](../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md), obtenga el auxiliar correspondiente al sitio especificado y, luego, obtenga el desplazamiento de documento inicial para el contexto de origen indicado de la manera siguiente:  
  
```  
pddh->GetScriptBlockInfo(dwSourceContext, NULL, &ulStartPos, NULL);  
```  
  
 Después, use el auxiliar para crear otro contexto de documento para el desplazamiento de caracteres especificado:  
  
```  
pddh->CreateDebugDocumentContext(ulStartPos + uCharacterOffset, cChars, &pddcNew);  
```  
  
 Para implementar [IActiveScriptSiteDebug::GetRootApplicationNode](../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md), basta con llamar a `IDebugApplication::GetRootNode`, que se hereda de [IRemoteDebugApplication::GetRootNode](../winscript/reference/iremotedebugapplication-getrootnode.md).  
  
 Para implementar [IDebugDocumentHelper::GetDebugApplicationNode](../winscript/reference/idebugdocumenthelper-getdebugapplicationnode.md), basta con devolver el elemento `IDebugApplication` creado inicialmente con el administrador de depuración del proceso.  
  
## <a name="the-optional-idebugdocumenthost-interface"></a>Interfaz IDebugDocumentHost opcional  
 El host puede proporcionar una implementación de la interfaz [IDebugDocumentHost (interfaz)](../winscript/reference/idebugdocumenthost-interface.md) mediante [IDebugDocumentHelper::SetDebugDocumentHost](../winscript/reference/idebugdocumenthelper-setdebugdocumenthost.md) para concederle mayor control sobre el auxiliar. Estos son algunos de los aspectos clave que la interfaz de host permite realizar:  
  
-   Agregue texto mediante [IDebugDocumentHelper::AddDeferredText](../winscript/reference/idebugdocumenthelper-adddeferredtext.md) para que el host no tenga que proporcionar los caracteres reales de inmediato. Cuando los caracteres sean realmente necesarios, el auxiliar llamará a [IDebugDocumentHost::GetDeferredText](../winscript/reference/idebugdocumenthost-getdeferredtext.md) en el host.  
  
-   Reemplace el color de sintaxis predeterminado que proporciona el auxiliar. El auxiliar llama a [IDebugDocumentHost::GetScriptTextAttributes](../winscript/reference/idebugdocumenthost-getscripttextattributes.md) para determinar el color de un intervalo de caracteres, que recurre a su implementación predeterminada si el host devuelve `E_NOTIMPL`.  
  
-   Especifique un control desconocido para contextos de documento creados por el auxiliar mediante la implementación de [IDebugDocumentHost::OnCreateDocumentContext](../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md). Esto permite al host reemplazar la funcionalidad de la implementación de contexto de documento predeterminada.  
  
-   Especifique un nombre de ruta de acceso en el sistema de archivos para el documento. Algunas interfaces de usuario de depuración utilizan esta ruta para permitir al usuario editar y guardar cambios en el documento. Una vez guardado el documento, se llama a [IDebugDocumentHost::NotifyChanged](../winscript/reference/idebugdocumenthost-notifychanged.md) para notificar al host.  
  
## <a name="see-also"></a>Vea también  
 [Información general acerca de la depuración de Active Script](../winscript/active-script-debugging-overview.md)