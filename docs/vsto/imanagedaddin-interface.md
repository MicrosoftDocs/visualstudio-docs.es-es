---
title: interfaz IManagedAddin
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IManagedAddin interface
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 89e705296c6051b8bdec823e523f0a386ff7ff76
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920441"
---
# <a name="imanagedaddin-interface"></a>interfaz IManagedAddin
  Implemente la interfaz IManagedAddin para crear un componente que cargue complementos de VSTO administrados. Esta interfaz se agregó en el sistema Microsoft Office de 2007.

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
 En la tabla siguiente se enumeran los métodos definidos por la interfaz IManagedAddin.

|Nombre|Descripción|
|----------|-----------------|
|[IManagedAddIn::Load](../vsto/imanagedaddin-load.md)|Se llama a este método cuando una aplicación de Microsoft Office carga un complemento de VSTO administrado.|
|[IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)|Se llama a este método justo antes de que una aplicación de Microsoft Office descargue un complemento de VSTO administrado.|

## <a name="remarks"></a>Notas
 Microsoft Office aplicaciones, a partir del sistema Microsoft Office 2007, use la interfaz IManagedAddin para ayudar a cargar los complementos de VSTO de Office. Puede implementar la interfaz IManagedAddin para crear su propio cargador de complementos de VSTO y tiempo de ejecución para los complementos de VSTO administrados, en lugar de usar el cargador de complementos de VSTO (*VSTOLoader.dll*) y [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Para obtener más información, consulta [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).

## <a name="how-managed-add-ins-are-loaded"></a>Cómo se cargan los complementos administrados
 Se producen los pasos siguientes cuando se inicia una aplicación:

1. La aplicación detecta los complementos de VSTO buscando las entradas en la siguiente clave del registro:

    **HKEY_CURRENT_USER\Software\Microsoft\Office\\ *\<application name>* \Addins\\**

    Cada entrada de esta clave del Registro es un identificador único del complemento de VSTO. Normalmente, se trata del nombre del ensamblado de complemento de VSTO.

2. La aplicación busca una entrada `Manifest` en la entrada de cada complemento de VSTO.

    Los complementos de VSTO administrados pueden almacenar la ruta de acceso completa de un manifiesto en la `Manifest` entrada en **HKEY_CURRENT_USER\Software\Microsoft\Office\\ _\<application name>_ \Addins \\ _\<add-in ID>_**. Un manifiesto es un archivo (normalmente un archivo XML) que ofrece información que se usa para cargar el complemento de VSTO.

3. Si la aplicación encuentra una entrada `Manifest` , la aplicación intenta cargar un componente de cargador de complemento de VSTO administrado. Para ello, la aplicación intenta crear un objeto COM que implementa la interfaz IManagedAddin.

    [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Incluye un componente de cargador de complementos de VSTO (*VSTOLoader.dll*) o puede crear el suyo propio implementando la interfaz IManagedAddin.

4. La aplicación llama al método [IManagedAddin::Load](../vsto/imanagedaddin-load.md) y pasa el valor de la entrada `Manifest` .

5. El método [IManagedAddin::Load](../vsto/imanagedaddin-load.md) realiza las tareas necesarias para cargar el complemento de VSTO, tales como la configuración de la directiva de seguridad y dominio de la aplicación para el complemento de VSTO que está cargando.

   Para obtener más información sobre las claves del registro que usan Microsoft Office aplicaciones para detectar y cargar complementos de VSTO administrados, consulte [entradas del registro para complementos de VSTO](../vsto/registry-entries-for-vsto-add-ins.md).

## <a name="guidance-to-implement-imanagedaddin"></a>Guía para implementar IManagedAddin
 Si implementa IManagedAddin, debe registrar el archivo DLL que contiene la implementación mediante el siguiente CLSID:

 99D651D7-5F7C-470E-8A3B-774D5D9536AC

 Microsoft Office aplicaciones utilizan este CLSID para crear el objeto COM que implementa IManagedAddin.

> [!CAUTION]
> Este CLSID también se usa en *VSTOLoader.dll* en [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Por lo tanto, si usa IManagedAddin para crear su propio componente de tiempo de ejecución y cargador de complementos de VSTO, no podrá implementar el componente en equipos que ejecuten complementos de VSTO que se basen en [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

## <a name="see-also"></a>Vea también
- [Referencia de la API no administrada &#40;desarrollo de Office en Visual Studio&#41;](../vsto/unmanaged-api-reference-office-development-in-visual-studio.md)
