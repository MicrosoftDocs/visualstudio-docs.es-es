---
title: "C&#243;mo: obtener un servicio de un subproceso en segundo plano (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "multithreading, servicios"
ms.assetid: 97a56709-66d4-431a-ae63-392ee5898511
caps.latest.revision: 8
caps.handback.revision: 8
manager: "douge"
---
# C&#243;mo: obtener un servicio de un subproceso en segundo plano (C++)
los servicios no se pueden obtener mediante `IServiceProvider.QueryService` de un subproceso de fondo.  Si utiliza `QueryService` para obtener un servicio en el subproceso principal y, a continuación intenta utilizar el servicio en un subproceso de fondo, también se producirá un error.  
  
 Para obtener un servicio desde un subproceso de fondo, utilice `CoMarshalInterThreadInterfaceInStream` en el método de `IVsPackage.SetSite` para formar el proveedor de servicios en una secuencia en el subproceso principal.  A continuación puede unmarshal el proveedor de servicios en un subproceso de fondo y utilizarlo para obtener el servicio.  Puede unmarshal solo una vez, por lo que almacena en caché la interfaz que recibirá.  
  
> [!NOTE]
>  El código administrado automáticamente forma interfaces entre los subprocesos, por lo que obtener un servicio desde un subproceso de fondo no requiere código especial.  
  
## Ejemplo  
 El código siguiente crea un proveedor de servicios en el subproceso principal y proporciona un método de `QueryServiceFromBackgroundThread` a unmarshal el proveedor de servicios para obtener un servicio desde un subproceso de fondo.  
  
```  
class CMyPackage : public IVsPackage  
{  
private:  
    // Used to marshal IServiceProvider between threads  
    CComPtr< IStream > m_pSPStream;  
    // IServiceProvider proxy for the background thread  
    CComPtr< IServiceProvider > m_pBackgroundSP;  
  
public:  
    HRESULT SetSite( IServiceProvider* pSP )  
    {  
        // Marshal the service provider into a stream so that  
        // the background thread can retrieve it later  
        CoMarshalInterThreadInterfaceInStream(  
            IID_IServiceProvider, pSP, &m_pSPStream);  
  
        //... do the rest of your initialization  
    }  
  
    // Call this when your background thread needs to call QueryService  
    // The first time through, it unmarshals the interface stored   
    HRESULT QueryServiceFromBackgroundThread(  
        REFGUID rsid,        // [in] Service ID  
        REFIID riid,         // [in] Interface ID  
        // [out] Interface pointer of requested service (NULL on error)  
        void **ppvObj  
    {  
        if( !m_pBackgroundSP )  
        {  
            if( !m_pSPStream )  
            {  
                return E_UNEXPECTED;  
            }  
  
            HRESULT hr = CoGetInterfaceAndReleaseStream(   
                m_pSPStream, IID_IServiceProvider,   
                (void **)&m_pBackgroundSP );  
            if( FAILED(hr) )  
            {  
                return hr;  
            }  
  
            // The CoGetInterfaceAndReleaseStream has already   
            // destroyed the stream.  To avoid double-freeing,   
            // the smart wrapper needs to be detached.  
            m_pSPStream.Detach();  
        }  
  
        return m_pBackgroundSP->QueryService( rsid, riid, ppvObj );  
    }  
};  
```  
  
## Vea también  
 [Utilizar y proporcionar servicios](../extensibility/using-and-providing-services.md)   
 [Fundamentos del servicio](../extensibility/internals/service-essentials.md)