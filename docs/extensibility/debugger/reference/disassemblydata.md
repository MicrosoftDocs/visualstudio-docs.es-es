---
description: Describe una instrucción de desensamblado para el entorno de desarrollo integrado (IDE) que se va a mostrar.
title: DisassemblyData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DisassemblyData
helpviewer_keywords:
- DisassemblyData structure
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 71d52c4f48f23368d83d81f88fba4bf0ba36f197
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096127"
---
# <a name="disassemblydata"></a>DisassemblyData
Describe una instrucción de desensamblado para el entorno de desarrollo integrado (IDE) que se va a mostrar.

## <a name="syntax"></a>Sintaxis

```cpp
typedef struct tagDisassemblyData {
    DISASSEMBLY_STREAM_FIELDS dwFields;
    BSTR                      bstrAddress;
    BSTR                      bstrAddressOffset;
    BSTR                      bstrCodeBytes;
    BSTR                      bstrOpcode;
    BSTR                      bstrOperands;
    BSTR                      bstrSymbol;
    UINT64                    uCodeLocationId;
    TEXT_POSITION             posBeg;
    TEXT_POSITION             posEnd;
    BSTR                      bstrDocumentUrl;
    DWORD                     dwByteOffset;
    DISASSEMBLY_FLAGS         dwFlags;
} DisassemblyData;
```

```csharp
public struct DisassemblyData { 
    public uint          dwFields;
    public string        bstrAddress;
    public string        bstrAddressOffset;
    public string        bstrCodeBytes;
    public string        bstrOpcode;
    public string        bstrOperands;
    public string        bstrSymbol;
    public ulong         uCodeLocationId;
    public TEXT_POSITION posBeg;
    public TEXT_POSITION posEnd;
    public string        bstrDocumentUrl;
    public uint          dwByteOffset;
    public uint          dwFlags;
};
```

## <a name="members"></a>Miembros
`dwFields`\
La constante [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) que especifica qué campos se rellenan.

`bstrAddress`\
La dirección como un desplazamiento desde algún punto de partida (normalmente, el principio de la función asociada).

`bstrCodeBytes`\
Bytes de código para esta instrucción.

`bstrOpcode`\
Código de operación para esta instrucción.

`bstrOperands`\
Operandos para esta instrucción.

`bstrSymbol`\
Nombre del símbolo, si existe, asociado a la dirección (símbolo público, etiqueta, etc.).

`uCodeLocationId`\
Identificador de ubicación del código para esta línea desensamblada. Si la dirección de contexto del código de una línea es mayor que la dirección de contexto del código de otra, el identificador de ubicación de código desensamblado de la primera también será mayor que el identificador de ubicación de código de la segunda.

`posBeg`\
[TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) que corresponde a la posición de un documento donde comienzan los datos del desensamblado.

`posEnd`\
[TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) que corresponde a la posición en un documento donde finalizan los datos del desensamblado.

`bstrDocumentUrl`\
En el caso de los documentos de texto que se pueden representar como nombres de archivo, el `bstrDocumentUrl` campo se rellena con el nombre de archivo donde se puede encontrar el origen, con el formato `file://file name` .

En el caso de los documentos de texto que no se pueden representar como nombres de archivo, `bstrDocumentUrl` es un identificador único para el documento y el motor de depuración debe implementar el método [getdocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md) .

Este campo también puede contener información adicional sobre las sumas de comprobación. Para obtener información detallada, vea la sección Comentarios de.

`dwByteOffset`\
Número de bytes de la instrucción desde el principio de la línea de código.

`dwFlags`\
La constante [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) que especifica qué marcas están activas.

## <a name="remarks"></a>Observaciones
Cada `DisassemblyData` estructura describe una instrucción del desensamblado. Una matriz de estas estructuras se devuelve desde el método [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) .

La estructura de [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) se utiliza solo para documentos basados en texto. El intervalo de código fuente de esta instrucción se rellena solo para la primera instrucción generada a partir de una instrucción o línea, por ejemplo, cuando `dwByteOffset == 0` .

En el caso de los documentos que no son de texto, se puede obtener un contexto de documento a partir del código y el `bstrDocumentUrl` campo debe ser un valor null. Si el `bstrDocumentUrl` campo es el mismo que el `bstrDocumentUrl` campo del elemento de la `DisassemblyData` matriz anterior, establezca `bstrDocumentUrl` en un valor null.

Si el `dwFlags` campo tiene `DF_DOCUMENT_CHECKSUM` establecida la marca, la información adicional de la suma de comprobación sigue la cadena a la que apunta el `bstrDocumentUrl` campo. En concreto, después del terminador de cadena null, sigue un GUID que identifica el algoritmo de suma de comprobación que a su vez va seguido de un valor de 4 bytes que indica el número de bytes de la suma de comprobación y que a su vez va seguido de los bytes de suma de comprobación. Vea el ejemplo de este tema sobre cómo codificar y descodificar este campo en [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] .

## <a name="example"></a>Ejemplo
El `bstrDocumentUrl` campo puede contener información adicional que no sea una cadena si `DF_DOCUMENT_CHECKSUM` se establece la marca. El proceso de creación y lectura de esta cadena codificada es sencillo en [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] . Sin embargo, en [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] , es otra cuestión. En el ejemplo siguiente se muestra una forma de crear la cadena codificada desde [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] y una manera de descodificar la cadena codificada en [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] .

```csharp
using System;
using System.Runtime.InteropServices;

namespace MyNamespace
{
    class MyClass
    {
        string EncodeData(string documentString,
                          Guid checksumGuid,
                          byte[] checksumData)
        {
            string returnString = documentString;

            if (checksumGuid == null || checksumData == null)
            {
                // Nothing more to do. Just return the string.
                return returnString;
            }

            returnString += '\0'; // separating null value

            // Add checksum GUID to string.
            byte[] guidDataArray  = checksumGuid.ToByteArray();
            int    guidDataLength = guidDataArray.Length;
            IntPtr pBuffer        = Marshal.AllocCoTaskMem(guidDataLength);
            for (int i = 0; i < guidDataLength; i++)
            {
                Marshal.WriteByte(pBuffer, i, guidDataArray[i]);
            }
            // Copy guid data bytes to string as wide characters.
            // Assumption: sizeof(char) == 2.
            for (int i = 0; i < guidDataLength / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }

            // Add checksum count (a 32-bit value).
            Int32 checksumCount = checksumData.Length;
            Marshal.StructureToPtr(checksumCount, pBuffer, true);
            for (int i = 0; i < sizeof(Int32) / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }

            // Add checksum data.
            pBuffer = Marshal.AllocCoTaskMem(checksumCount);
            for (int i = 0; i < checksumCount; i++)
            {
                Marshal.WriteByte(pBuffer, i, checksumData[i]);
            }
            for (int i = 0; i < checksumCount / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }
            Marshal.FreeCoTaskMem(pBuffer);

            return returnString;
        }

        void DecodeData(    string encodedString,
                        out string documentString,
                        out Guid   checksumGuid,
                        out byte[] checksumData)
        {
            documentString = String.Empty;
            checksumGuid = Guid.Empty;
            checksumData = null;

            IntPtr pBuffer = Marshal.StringToBSTR(encodedString);
            if (null != pBuffer)
            {
                int bufferOffset = 0;

                // Parse string out. String is assumed to be Unicode.
                documentString = Marshal.PtrToStringUni(pBuffer);
                bufferOffset += (documentString.Length + 1) * sizeof(char);

                // Parse Guid out.
                // Read guid bytes from buffer and store in temporary
                // buffer that contains only the guid bytes. Then the
                // Marshal.PtrToStructure() can work properly.
                byte[] guidDataArray  = checksumGuid.ToByteArray();
                int    guidDataLength = guidDataArray.Length;
                IntPtr pGuidBuffer    = Marshal.AllocCoTaskMem(guidDataLength);
                for (int i = 0; i < guidDataLength; i++)
                {
                    Marshal.WriteByte(pGuidBuffer, i,
                                      Marshal.ReadByte(pBuffer, bufferOffset + i));
                }
                bufferOffset += guidDataLength;
                checksumGuid = (Guid)Marshal.PtrToStructure(pGuidBuffer, typeof(Guid));
                Marshal.FreeCoTaskMem(pGuidBuffer);

                // Parse out the number of checksum data bytes (always 32-bit value).
                int dataCount = Marshal.ReadInt32(pBuffer, bufferOffset);
                bufferOffset += sizeof(Int32);

                // Parse out the checksum data.
                checksumData = new byte[dataCount];
                for (int i = 0; i < dataCount; i++)
                {
                    checksumData[i] = Marshal.ReadByte(pBuffer, bufferOffset + i);
                }
            }
        }
    }
}
```

## <a name="see-also"></a>Consulte también
- [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)
- [Lectura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
