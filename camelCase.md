**განსაზღვრა:** იდენტიფიკატორი, სადაც **პირველი სიტყვის** პირველი ასო **პატარაა**, შემდეგი სიტყვების — **დიდი**. напр.: `userId`, `retryCount`, `cancellationToken`.

**სად გამოიყენება (.NET/C#):**

- **პარამეტრები და ლოკალური ცვლადები**.
    
- **Private ველები** — ხშირად `_camelCase` პრეფიქსით (`_userRepository`).


public async Task<bool> TryConfirmAsync(OrderId orderId, int retryCount, CancellationToken cancellationToken)
{
    for (var attempt = 0; attempt < retryCount; attempt++)
    {
        var success = await ConfirmInternalAsync(orderId, cancellationToken);
        if (success) return true;
    }
    return false;
}
