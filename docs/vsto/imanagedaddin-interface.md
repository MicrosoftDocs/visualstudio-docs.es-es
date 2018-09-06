---
title: interfaz IManagedAddin
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IManagedAddin interface
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b113d0d62156d77d08fa2fcdbb415d0518eba3a8
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "35673946"
---
# <a name="imanagedaddin-interface"></a>interfaz IManagedAddin
  Implementar la interfaz IManagedAddin para crear un componente que carga administrados complementos de VSTO. Esta interfaz se agregó en 2007 Microsoft Office system.  
  
## <a name="syntax"></a>Sintaxis  
  
```csharp
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
  
## <a name="methods"></a>Métodos  
 En la tabla siguiente se enumera los métodos que se definen mediante la interfaz IManagedAddin.  
  
|nombre|Descripción|  
|----------|-----------------|  
|[IManagedAddin::Load](../vsto/imanagedaddin-load.md)|Se llama a este método cuando una aplicación de Microsoft Office carga un complemento de VSTO administrado.|  
|[IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)|Se llama a este método justo antes de que una aplicación de Microsoft Office descargue un complemento de VSTO administrado.|  
  
## <a name="remarks"></a>Comentarios  
 Aplicaciones de Microsoft Office, empezando por el sistema Microsoft Office 2007, use la interfaz IManagedAddin para ayudar a cargar complementos de VSTO de Office. Puede implementar la interfaz IManagedAddin para crear su propio cargador de complementos de VSTO y tiempo de ejecución para administra complementos VSTO, en lugar de usar el cargador de complementos de VSTO (*VSTOLoader.dll*) y [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Para obtener más información, consulta [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).  
  
## <a name="how-managed-add-ins-are-loaded"></a>Cómo se cargan los complementos administrados  
 Se producen los pasos siguientes cuando se inicia una aplicación:  
  
1.  La aplicación detecta los complementos de VSTO buscando las entradas en la siguiente clave del registro:  
  
     **HKEY_CURRENT_USER\Software\Microsoft\Office\\_\<nombreDeAplicación >_ \Addins\**  
  
     Cada entrada de esta clave del Registro es un identificador único del complemento de VSTO. Normalmente, se trata del nombre del ensamblado de complemento de VSTO.  
  
2.  La aplicación busca una entrada `Manifest` en la entrada de cada complemento de VSTO.  
  
     Complementos VSTO administrados pueden almacenar la ruta de acceso completa de un manifiesto en el `Manifest` entrada bajo **HKEY_CURRENT_USER\Software\Microsoft\Office\\_\<nombreDeAplicación >_ \Addins\\  _\<ID de complemento >_**. Un manifiesto es un archivo (normalmente un archivo XML) que proporciona información que se usa para cargar el complemento VSTO.  
  
3.  Si la aplicación encuentra una entrada `Manifest` , la aplicación intenta cargar un componente de cargador de complemento de VSTO administrado. Para ello, la aplicación intenta crear un objeto COM que implementa la interfaz IManagedAddin.  
  
     El [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] incluye un componente de cargador de complementos de VSTO (*VSTOLoader.dll*), o bien puede crear los suyos propios al implementar la interfaz IManagedAddin.  
  
4.  La aplicación llama al método [IManagedAddin::Load](../vsto/imanagedaddin-load.md) y pasa el valor de la entrada `Manifest` .  
  
5.  El método [IManagedAddin::Load](../vsto/imanagedaddin-load.md) realiza las tareas necesarias para cargar el complemento de VSTO, tales como la configuración de la directiva de seguridad y dominio de la aplicación para el complemento de VSTO que está cargando.  
  
 Para obtener más información sobre el registro de las claves que usan aplicaciones de Microsoft Office detecte y cargue administran complementos VSTO, consulte [entradas del registro para complementos VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  
  
## <a name="guidance-to-implement-imanagedaddin"></a>Guía para implementar IManagedAddin  
 Si decide implementar IManagedAddin, debe registrar la DLL que contiene la implementación mediante el siguiente CLSID:  
  
 99D651D7-5F7C-470E-8A3B-774D5D9536AC  
  
 Aplicaciones de Microsoft Office utilizan este CLSID para crear el objeto COM que implementa IManagedAddin.  
  
> [!CAUTION]  
>  También utiliza este CLSID *VSTOLoader.dll* en el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Por lo tanto, si usas IManagedAddin para crear su propio cargador de complementos de VSTO y el componente en tiempo de ejecución, no se puede implementar el componente en equipos que ejecutan complementos VSTO que se basan en el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
## <a name="see-also"></a>Vea también  
 [Referencia de API no administrada &#40;desarrollo de Office en Visual Studio&#41;](../vsto/unmanaged-api-reference-office-development-in-visual-studio.md)  
  
  