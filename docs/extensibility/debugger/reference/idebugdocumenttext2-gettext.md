---
title: 'IDebugDocumentText2:: GetText | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2::GetText
helpviewer_keywords:
- IDebugDocumentText2::GetText
ms.assetid: f8c15a58-da77-473e-a721-7a094e306c63
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2429bdf3f09eff168210a7b835a9e506d74d63ea
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80731576"
---
# <a name="idebugdocumenttext2gettext"></a>IDebugDocumentText2::GetText
Recupera el texto de la posición especificada en el documento.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetText(
    TEXT_POSITION pos,
    ULONG         cMaxChars,
    WCHAR*        pText,
    ULONG*        pcNumChars
);
```

```csharp
int GetText(
    eumn_TEXT_POSITION pos,
    uint               cMaxChars,
    IntPtr             pText,
    out uint           pcNumChars
);
```

## <a name="parameters"></a>Parámetros
`pos`\
de Estructura de [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) que indica la ubicación del texto que se va a recuperar.

`cMaxChars`\
de Número máximo de caracteres del texto que se va a recuperar.

`pText`\
[in, out] Puntero a un búfer que se va a rellenar con el texto deseado. Este búfer debe ser capaz de contener al menos un `cMaxChars` número de caracteres anchos.

`pcNumChars`\
enuncia Devuelve el número de caracteres que se han recuperado realmente.

## <a name="return-value"></a>Valor devuelto
Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="example"></a>Ejemplo
En este ejemplo se muestra cómo se puede llamar a este método desde C#.

```csharp
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio;
using Microsoft.VisualStudio.Debugger.Interop;

namespace Mynamespace
{
    class MyClass
    {
        string GetDocumentText(IDebugDocumentText2 pText, TEXT_POSITION pos)
        {
            string documentText = string.Empty;
            if (pText != null)
            {
                uint numLines = 0;
                uint numChars = 0;
                int hr;
                hr = pText.GetSize(ref numLines, ref numChars);
                if (ErrorHandler.Succeeded(hr))
                {
                    IntPtr buffer = Marshal.AllocCoTaskMem((int)numChars * sizeof(char));
                    uint actualChars = 0;
                    hr = pText.GetText(pos, numChars, buffer, out actualChars);
                    if (ErrorHandler.Succeeded(hr))
                    {
                        documentText = Marshal.PtrToStringUni(buffer, (int)actualChars);
                    }
                    Marshal.FreeCoTaskMem(buffer);
                }
            }
            return documentText;
        }
    }
}
```

## <a name="see-also"></a>Vea también
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
