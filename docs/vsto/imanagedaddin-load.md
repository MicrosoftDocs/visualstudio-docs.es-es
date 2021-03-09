---
title: IManagedAddIn::Load
description: Se llama a este elemento cuando se carga un complemento VSTO administrado.
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
helpviewer_keywords: ''
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fc89ba13e9fc0f62b264cdb926e1a8392c0b41bd
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2021
ms.locfileid: "102469767"
---
# <a name="imanagedaddinload"></a>IManagedAddIn::Load
  Se llama a este elemento cuando se carga un complemento VSTO administrado.

## <a name="syntax"></a>Sintaxis

```csharp
HRESULT Load([in] BSTR bstrManifestURL,
             [in] IDispatch *pdispApplication);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*bstrManifestURL*|Ruta de acceso del manifiesto del complemento VSTO.|
|*pdispApplication*|Un puntero a un IDispatch que representa la aplicación host que está cargando el complemento de VSTO.|

## <a name="return-value"></a>Valor devuelto
 Un valor HRESULT que indica si el método se ha completado correctamente.

## <a name="remarks"></a>Observaciones
 Un manifiesto es un archivo (normalmente un archivo XML) que ofrece información que se usa para cargar el complemento de VSTO. Por ejemplo, un manifiesto puede especificar la ubicación del ensamblado del complemento VSTO y la clase de punto de entrada, para así poder crear una instancia cuando se carga el complemento VSTO.

 El parámetro *bstrManifestURL* contiene el valor de la `Manifest` entrada en la clave del registro **HKEY_CURRENT_USER\Software\Microsoft\Office\\ _\<application name>_ \Addins \\ _\<add-in ID>_** para el complemento de VSTO. Para obtener más información, consulte [interfaz IManagedAddin](../vsto/imanagedaddin-interface.md).

 Implemente el método [IManagedAddIn::Load](../vsto/imanagedaddin-load.md) para realizar tareas como configurar el dominio de la aplicación y la directiva de seguridad del complemento VSTO que se va a cargar.

## <a name="see-also"></a>Vea también
- [interfaz IManagedAddin](../vsto/imanagedaddin-interface.md)
- [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)
