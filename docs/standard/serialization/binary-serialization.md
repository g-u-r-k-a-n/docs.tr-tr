---
title: İkili serileştirme
description: Bu makalede, .NET Core 'un desteklediği ikili serileştirme ve türler açıklanır. İkili serileştirme ve alternatiflerin tehlikeleri hakkında farkında olun.
ms.date: 01/02/2018
helpviewer_keywords:
- binary serialization
- serialization, about serialization
- deserialization
- binary serialization, about serialization
- binary serialization, .net core serialization
- serialization, cross-framework
ms.assetid: 2b1ea3be-1152-4032-b2b3-07794054c405
author: ViktorHofer
ms.openlocfilehash: c735d30920fd3c8cd13243b4a5a29489ce05b262
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "84289700"
---
# <a name="binary-serialization"></a>İkili serileştirme

Serileştirme depolama ortamına bir nesne durumunu depolama işlemi olarak tanımlanabilir. Bu işlem sırasında, nesnenin ortak ve özel alanları ile sınıfın adı, sınıfı içeren derleme dahil olmak üzere, bir veri akışına yazılan bayt akışına dönüştürülür. Nesnenin seri durumdan daha sonra orijinal nesneyi tam bir kopyası oluşturulur.

Bir serileştirme mekanizmasını nesne yönelimli bir ortamda uygularken, kullanım kolaylığı ve esneklik arasında bir dizi denge yapmanız gerekir. Süreç üzerinde yeterli denetim verildiğinden işlem, büyük bir ölçüde otomatik olabilir. Örneğin, burada basit ikili serileştirme yeterli değil veya bir sınıf hangi alanları seri hale gerek karar vermek için belirli bir neden olabilir durumlarda gerçekleşebilir. Aşağıdaki bölümlerde .NET ile sunulan güçlü serileştirme mekanizması incelenecektir ve bu işlemi gereksinimlerinizi karşılayacak şekilde özelleştirmenize imkan tanıyan bazı önemli özellikler vurgulanacak.

> [!NOTE]
> Nesnenin serileştirildiği ve farklı .NET Framework sürümleri kullanılarak seri durumdan UTF-8 veya UTF-7 kodlanmış nesne durumunu korunur değil.

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

İkili serileştirme bir nesne içindeki özel üyelerin değiştirilmesini ve bu nedenle durumunun değiştirilmesini sağlar. Bu nedenle, <xref:System.Text.Json?displayProperty=fullName> ortak API yüzeyinde çalışan gibi diğer serileştirme çerçeveleri önerilir.

## <a name="net-core"></a>.NET Core

.NET Core bir tür alt kümesi için ikili serileştirme destekler. Desteklenen türlerin listesini aşağıdaki [seri hale getirilebilir türler](#serializable-types) bölümünde görebilirsiniz. Listelenen türlerin .NET Framework 4.5.1 ve sonraki sürümleri ile .NET Core 2,0 ve sonraki sürümleri arasında seri hale getirilebilir olduğu garanti edilir. Mono gibi diğer .NET uygulamaları resmi olarak desteklenmez, ancak aynı zamanda çalışmalıdır.

### <a name="serializable-types"></a>Serileştirilebilir türler

> [!div class="mx-tdCol2BreakAll"]
> | Tür | Notlar |
> | - | - |
> | <xref:Microsoft.CSharp.RuntimeBinder.RuntimeBinderException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:Microsoft.CSharp.RuntimeBinder.RuntimeBinderInternalCompilerException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.AccessViolationException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.AggregateException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.AppDomainUnloadedException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.ApplicationException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.ArgumentException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.ArgumentNullException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.ArgumentOutOfRangeException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.ArithmeticException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Array?displayProperty=nameWithType> | |
> | <xref:System.ArraySegment%601?displayProperty=nameWithType> | |
> | <xref:System.ArrayTypeMismatchException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Attribute?displayProperty=nameWithType> | |
> | <xref:System.BadImageFormatException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Boolean?displayProperty=nameWithType> | |
> | <xref:System.Byte?displayProperty=nameWithType> | |
> | <xref:System.CannotUnloadAppDomainException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Char?displayProperty=nameWithType> | |
> | <xref:System.Collections.ArrayList?displayProperty=nameWithType> | |
> | <xref:System.Collections.BitArray?displayProperty=nameWithType> | |
> | <xref:System.Collections.Comparer?displayProperty=nameWithType> | |
> | <xref:System.Collections.DictionaryEntry?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Comparer%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.EqualityComparer%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.HashSet%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Collections.Generic.KeyValuePair%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.LinkedList%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.SortedSet%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Stack%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Hashtable?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.Collection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Queue?displayProperty=nameWithType> | |
> | <xref:System.Collections.SortedList?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.HybridDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.ListDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.StringCollection?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.StringDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Stack?displayProperty=nameWithType> | |
> | `System.Collections.Generic.NonRandomizedStringEqualityComparer` | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.ComponentModel.BindingList%601?displayProperty=nameWithType> | |
> | <xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.ComponentModel.Design.CheckoutException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.ComponentModel.InvalidAsynchronousStateException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.ComponentModel.LicenseException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak.<br/>.NET Framework 'den .NET Core 'a serileştirme desteklenmez. |
> | <xref:System.ComponentModel.WarningException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.ComponentModel.Win32Exception?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Configuration.ConfigurationErrorsException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Configuration.ConfigurationException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Configuration.Provider.ProviderException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Configuration.SettingsPropertyIsReadOnlyException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Configuration.SettingsPropertyNotFoundException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Configuration.SettingsPropertyWrongTypeException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.ContextMarshalException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.DBNull?displayProperty=nameWithType> | .NET Core 2.0.2 ve sonraki sürümlerde başlatılıyor. |
> | <xref:System.Data.Common.DbException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Data.ConstraintException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Data.DBConcurrencyException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Data.DataException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Data.DataSet?displayProperty=nameWithType> | |
> | <xref:System.Data.DataTable?displayProperty=nameWithType> | ' A ayarlarsanız `RemotingFormat` `SerializationFormat.Binary` , yalnızca .net Core 2,1 ve sonraki sürümlerle değiş tokuş edilebilir. |
> | <xref:System.Data.DeletedRowInaccessibleException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Data.DuplicateNameException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Data.EvaluateException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Data.InRowChangingEventException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Data.InvalidConstraintException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Data.InvalidExpressionException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Data.MissingPrimaryKeyException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Data.NoNullAllowedException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Data.Odbc.OdbcException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Data.OperationAbortedException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Data.PropertyCollection?displayProperty=nameWithType> | |
> | <xref:System.Data.ReadOnlyException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Data.RowNotInTableException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Data.SqlClient.SqlException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak.<br/>.NET Framework 'den .NET Core 'a serileştirme desteklenmez |
> | <xref:System.Data.SqlTypes.SqlAlreadyFilledException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Data.SqlTypes.SqlBoolean?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlByte?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlDateTime?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlDouble?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlGuid?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt16?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt32?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt64?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlNotFilledException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Data.SqlTypes.SqlNullValueException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Data.SqlTypes.SqlString?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlTruncateException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Data.SqlTypes.SqlTypeException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Data.StrongTypingException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Data.SyntaxErrorException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Data.VersionNotFoundException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.DataMisalignedException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.DateTime?displayProperty=nameWithType> | |
> | <xref:System.DateTimeOffset?displayProperty=nameWithType> | |
> | <xref:System.Decimal?displayProperty=nameWithType> | |
> | `System.Diagnostics.Contracts.ContractException` | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Diagnostics.Tracing.EventSourceException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.IO.DirectoryNotFoundException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.DirectoryServices.AccountManagement.MultipleMatchesException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.DirectoryServices.AccountManagement.NoMatchingPrincipalException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.DirectoryServices.AccountManagement.PasswordException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalExistsException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalOperationException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalServerDownException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryObjectExistsException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryObjectNotFoundException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryOperationException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryServerDownException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.DirectoryServices.ActiveDirectory.ForestTrustCollisionException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.DirectoryServices.ActiveDirectory.SyncFromAllServersOperationException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.DirectoryServices.DirectoryServicesCOMException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.DirectoryServices.Protocols.BerConversionException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.DirectoryServices.Protocols.DirectoryException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.DirectoryServices.Protocols.DirectoryOperationException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.DirectoryServices.Protocols.LdapException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.DirectoryServices.Protocols.TlsOperationException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.DivideByZeroException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.DllNotFoundException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Double?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Color?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Point?displayProperty=nameWithType> | |
> | <xref:System.Drawing.PointF?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Rectangle?displayProperty=nameWithType> | |
> | <xref:System.Drawing.RectangleF?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Size?displayProperty=nameWithType> | |
> | <xref:System.Drawing.SizeF?displayProperty=nameWithType> | |
> | <xref:System.DuplicateWaitObjectException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.EntryPointNotFoundException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Enum?displayProperty=nameWithType> | |
> | <xref:System.EventArgs?displayProperty=nameWithType> | .NET Core 2.0.6 'tan başlayarak. |
> | <xref:System.Exception?displayProperty=nameWithType> | |
> | <xref:System.ExecutionEngineException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.FieldAccessException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.FormatException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> | |
> | <xref:System.Globalization.CultureNotFoundException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Globalization.SortVersion?displayProperty=nameWithType> | |
> | <xref:System.Guid?displayProperty=nameWithType> | |
> | `System.IO.Compression.ZLibException` | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.IO.DriveNotFoundException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.IO.EndOfStreamException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.IO.FileFormatException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.IO.FileLoadException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.IO.FileNotFoundException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.IO.IOException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.IO.InternalBufferOverflowException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.IO.InvalidDataException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.IO.IsolatedStorage.IsolatedStorageException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.IO.PathTooLongException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.IndexOutOfRangeException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.InsufficientExecutionStackException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.InsufficientMemoryException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Int16?displayProperty=nameWithType> | |
> | <xref:System.Int32?displayProperty=nameWithType> | |
> | <xref:System.Int64?displayProperty=nameWithType> | |
> | <xref:System.IntPtr?displayProperty=nameWithType> | |
> | <xref:System.InvalidCastException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.InvalidOperationException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.InvalidProgramException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.InvalidTimeZoneException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.MemberAccessException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.MethodAccessException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.MissingFieldException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.MissingMemberException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.MissingMethodException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.MulticastNotSupportedException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Net.Cookie?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieCollection?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieContainer?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Net.HttpListenerException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Net.Mail.SmtpException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Net.Mail.SmtpFailedRecipientException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Net.Mail.SmtpFailedRecipientsException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Net.NetworkInformation.NetworkInformationException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Net.NetworkInformation.PingException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Net.ProtocolViolationException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Net.Sockets.SocketException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Net.WebException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Net.WebSockets.WebSocketException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.NotFiniteNumberException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.NotImplementedException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.NotSupportedException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.NullReferenceException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Nullable%601?displayProperty=nameWithType> | |
> | <xref:System.Numerics.BigInteger?displayProperty=nameWithType> | |
> | <xref:System.Numerics.Complex?displayProperty=nameWithType> | |
> | <xref:System.Object?displayProperty=nameWithType> | |
> | <xref:System.ObjectDisposedException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.OperationCanceledException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.OutOfMemoryException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.OverflowException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.PlatformNotSupportedException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.RankException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Reflection.AmbiguousMatchException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Reflection.CustomAttributeFormatException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Reflection.InvalidFilterCriteriaException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Reflection.ReflectionTypeLoadException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak.<br/>.NET Framework 'den .NET Core 'a serileştirme desteklenmez. |
> | <xref:System.Reflection.TargetException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Reflection.TargetInvocationException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Reflection.TargetParameterCountException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Resources.MissingManifestResourceException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Resources.MissingSatelliteAssemblyException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Runtime.CompilerServices.RuntimeWrappedException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Runtime.InteropServices.COMException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Runtime.InteropServices.ExternalException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Runtime.InteropServices.InvalidComObjectException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Runtime.InteropServices.InvalidOleVariantTypeException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Runtime.InteropServices.MarshalDirectiveException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Runtime.InteropServices.SEHException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Runtime.Serialization.InvalidDataContractException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Runtime.Serialization.SerializationException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.SByte?displayProperty=nameWithType> | |
> | <xref:System.Security.AccessControl.PrivilegeNotHeldException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Security.Authentication.AuthenticationException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Security.Authentication.InvalidCredentialException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Security.Cryptography.CryptographicException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Security.Cryptography.CryptographicUnexpectedOperationException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | `System.Security.Cryptography.Xml.CryptoSignedXmlRecursionException` | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Security.HostProtectionException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Security.Policy.PolicyException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Security.Principal.IdentityNotMappedException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Security.SecurityException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak.<br/>Sınırlı serileştirme verileri. |
> | <xref:System.Security.VerificationException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Security.XmlSyntaxException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.ServiceProcess.TimeoutException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Single?displayProperty=nameWithType> | |
> | <xref:System.StackOverflowException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.String?displayProperty=nameWithType> | |
> | <xref:System.StringComparer?displayProperty=nameWithType> | |
> | <xref:System.SystemException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Text.DecoderFallbackException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Text.EncoderFallbackException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Text.RegularExpressions.RegexMatchTimeoutException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Text.StringBuilder?displayProperty=nameWithType> | |
> | <xref:System.Threading.AbandonedMutexException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Threading.BarrierPostPhaseException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Threading.LockRecursionException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Threading.SemaphoreFullException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Threading.SynchronizationLockException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Threading.Tasks.TaskCanceledException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Threading.Tasks.TaskSchedulerException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Threading.ThreadAbortException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Threading.ThreadInterruptedException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Threading.ThreadStartException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Threading.ThreadStateException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Threading.WaitHandleCannotBeOpenedException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.TimeSpan?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneInfo.AdjustmentRule?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneInfo?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneNotFoundException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.TimeoutException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Transactions.TransactionAbortedException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Transactions.TransactionException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Transactions.TransactionInDoubtException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Transactions.TransactionManagerCommunicationException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Transactions.TransactionPromotionException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Tuple?displayProperty=nameWithType> | |
> | <xref:System.TypeAccessException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.TypeInitializationException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.TypeLoadException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.TypeUnloadedException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.UInt16?displayProperty=nameWithType> | |
> | <xref:System.UInt32?displayProperty=nameWithType> | |
> | <xref:System.UInt64?displayProperty=nameWithType> | |
> | <xref:System.UIntPtr?displayProperty=nameWithType> | |
> | <xref:System.UnauthorizedAccessException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Uri?displayProperty=nameWithType> | |
> | <xref:System.UriFormatException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.ValueTuple?displayProperty=nameWithType> | .NET Framework 4,7 ve önceki sürümlerde seri hale getirilebilir değildir. |
> | <xref:System.ValueType?displayProperty=nameWithType> | |
> | <xref:System.Version?displayProperty=nameWithType> | |
> | <xref:System.WeakReference%601?displayProperty=nameWithType> | |
> | <xref:System.WeakReference?displayProperty=nameWithType> | |
> | <xref:System.Xml.Schema.XmlSchemaException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Xml.Schema.XmlSchemaInferenceException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Xml.Schema.XmlSchemaValidationException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Xml.XPath.XPathException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Xml.XmlException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Xml.Xsl.XsltCompileException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |
> | <xref:System.Xml.Xsl.XsltException?displayProperty=nameWithType> | .NET Core 2.0.4 'tan başlayarak. |

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization>\
Serileştirme ve seri kaldırma nesneler için kullanılan sınıfları içerir.

- [XML ve SOAP serileştirme](xml-and-soap-serialization.md)\
Ortak dil çalışma zamanı ile içerdiği XML serileştirme mekanizması açıklanmaktadır.

- [Güvenlik ve serileştirme](../../framework/misc/security-and-serialization.md)\
Serileştirme gerçekleştiren kod yazarken izlemek için güvenli kodlama yönergeleri açıklar.

- [.NET uzaktan Iletişim](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))\
Uzak iletişimler için .NET Framework başlayarak çeşitli yöntemleri açıklar.

- [ASP.NET ve XML Web hizmeti Istemcileri kullanılarak oluşturulan XML Web Hizmetleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))\
ASP.NET kullanılarak oluşturulan XML Web hizmetlerinin programlamasını açıklayan ve açıklayan makaleler.
