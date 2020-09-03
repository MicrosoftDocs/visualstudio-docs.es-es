---
title: IManagedAddIn::Load
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
helpviewer_keywords: ''
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1307d720e005855770ee68659374dbbfae247d65
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85541042"
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

 El parámetro *bstrManifestURL* contiene el valor de la `Manifest` entrada en la clave del registro **HKEY_CURRENT_USER \software\microsoft\office \\ _\<application name>_ \Addins \\ _\<add-in ID>_ ** para el complemento de VSTO. Para obtener más información, consulte [interfaz IManagedAddin](../vsto/imanagedaddin-interface.md).

 Implemente el método [IManagedAddIn::Load](../vsto/imanagedaddin-load.md) para realizar tareas como configurar el dominio de la aplicación y la directiva de seguridad del complemento VSTO que se va a cargar.

## <a name="see-also"></a>Consulte también
- [IManagedAddin Interface](../vsto/imanagedaddin-interface.md)
- [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)
