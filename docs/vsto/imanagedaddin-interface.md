---
title: "Interfaz IManagedAddin"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "interfaz IManagedAddin"
ms.assetid: 5350629c-6cf8-42dd-ae65-3f34322ee10f
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# Interfaz IManagedAddin
  Implemente la interfaz IManagedAddin para crear un componente que cargue complementos de VSTO administrados. Esta interfaz se agregó en 2007 Microsoft Office system.  
  
## Sintaxis  
  
```  
[  
    object,  
    uuid(B9CEAB65-331C-4713-8410-DDDAF8EC191A),  
    pointer_default(unique),  
    oleautomation  
]  
interface IManagedAddin : IUnknown  
{  
    HRESULT Load(  
        [in] BSTR bstrManifestURL,   
        [in] IDispatch *pdispApplication);  
    HRESULT Unload();  
};  
```  
  
## Métodos  
 En la tabla siguiente se enumeran los métodos que define la interfaz IManagedAddin.  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[IManagedAddin::Load](../vsto/imanagedaddin-load.md)|Se llama a este método cuando una aplicación de Microsoft Office carga un complemento de VSTO administrado.|  
|[IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)|Se llama a este método justo antes de que una aplicación de Microsoft Office descargue un complemento de VSTO administrado.|  
  
## Comentarios  
 Las aplicaciones de Microsoft Office, a partir de 2007 Microsoft Office system, utilizan la interfaz IManagedAddin para ayudar a cargar complementos de VSTO de Office. Puede implementar la interfaz IManagedAddin para crear un tiempo de ejecución y un cargador de complemento de VSTO propios para complementos de VSTO administrados, en lugar de utilizar el cargador de complemento de VSTO \(VSTOLoader.dll\) y [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Para obtener más información, consulta [Arquitectura de complementos de VSTO](../vsto/architecture-of-vsto-add-ins.md).  
  
## Cómo se cargan los complementos administrados  
 Se producen los pasos siguientes cuando se inicia una aplicación:  
  
1.  La aplicación detecta los complementos de VSTO buscando las entradas en la siguiente clave del registro:  
  
     HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\*\<nombre de aplicación\>*\\Addins\\  
  
     Cada entrada de esta clave del Registro es un identificador único del complemento de VSTO. Normalmente, se trata del nombre del ensamblado de complemento de VSTO.  
  
2.  La aplicación busca una entrada `Manifest` en la entrada de cada complemento de VSTO.  
  
     Los complementos de VSTO administrados pueden almacenar la ruta completa de un manifiesto en la entrada `Manifest`, HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\*\<nombre de aplicación\>*\\Addins\\*\<Id. de complemento\>*. Un manifiesto es un archivo \(normalmente un archivo XML\) que ofrece información que se usa para cargar el complemento de VSTO.  
  
3.  Si la aplicación encuentra una entrada `Manifest`, la aplicación intenta cargar un componente de cargador de complemento de VSTO administrado. Para ello, la aplicación intenta crear un objeto COM que implementa la interfaz IManagedAddin.  
  
     [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] incluye un componente de cargador de complemento de VSTO \(VSTOLoader.dll\) o puede crear el suyo propio si implementa la interfaz IManagedAddin.  
  
4.  La aplicación llama al método [IManagedAddin::Load](../vsto/imanagedaddin-load.md) y pasa el valor de la entrada `Manifest`.  
  
5.  El método [IManagedAddin::Load](../vsto/imanagedaddin-load.md) realiza las tareas necesarias para cargar el complemento de VSTO, tales como la configuración de la directiva de seguridad y dominio de la aplicación para el complemento de VSTO que está cargando.  
  
 Para más información sobre las claves del Registro que las aplicaciones de Microsoft Office utilizan para detectar y cargar complementos de VSTO administrados, consulte [Entradas del registro para complementos de VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  
  
## Guía para implementar IManagedAddin  
 Si implementa IManagedAddin, debe registrar la DLL que contiene la implementación mediante el siguiente CLSID:  
  
 99D651D7\-5F7C\-470E\-8A3B\-774D5D9536AC  
  
 Las aplicaciones de Microsoft Office utilizan este CLSID para crear el objeto COM que implementa IManagedAddin.  
  
> [!CAUTION]  
>  VSTOLoader.dll también utiliza este CLSID en [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Por lo tanto, si utiliza IManagedAddin para crear su propio componente de tiempo de ejecución y cargador de complemento de VSTO, no podrá implementar el componente en equipos que ejecuten complementos de VSTO que dependen de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
## Vea también  
 [Referencia de la API administrada &#40;desarrollo de Office en Visual Studio&#41;](../vsto/unmanaged-api-reference-office-development-in-visual-studio.md)  
  
  