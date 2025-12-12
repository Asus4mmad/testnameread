
# testnameread

<table dir="rtl">
  <thead>
    <tr>
      <th rowspan="2">ردیف</th>
      <th colspan="2">تغییرات مربوط به افزودن روش جدید پرداخت</th>
      <th colspan="2">تغییرات مربوط به افزودن روش جدید ارسال پیام</th>
    </tr>
    <tr>
      <th>کلاس تغییر یافته</th>
      <th>توضیح کوتاه در مورد تغییر</th>
      <th>کلاس تغییر یافته</th>
      <th>توضیح کوتاه در مورد تغییر</th>
    </tr>
  </thead>

  <tbody>
    <!-- ردیف 1 (SMS) - بدون تغییر + پرداخت جدید اضافه شد -->
    <tr>
      <td>1</td>
      <td><code>PaymentProcessor</code></td>
      <td>افزودن متد جدید پرداخت حضوری: <code>payInPerson(double amount)</code> و چاپ پیام <code>Paid in person: ...</code></td>
      <td><code>ReservationService.java</code></td>
      <td>اضافه شدن شاخه <code>case SMS</code> و ساخت <code>SmsSender</code> و فراخوانی <code>sendSms(res.customer.mobile, "Your reservation confirmed!")</code> و چاپ پیام موفقیت.</td>
    </tr>

    <!-- ردیف 2 (SMS) - بدون تغییر + پرداخت جدید اضافه شد -->
    <tr>
      <td>2</td>
      <td><code>ReservationService.java</code></td>
      <td>افزودن شاخه <code>case ONSITE</code> و فراخوانی <code>paymentProcessor.payInPerson(res.totalPrice())</code></td>
      <td><code>MessageSender.java</code></td>
      <td>اضافه شدن امضای متد: <code>public void sendSms(String phoneNumber, String message);</code></td>
    </tr>

    <!-- ردیف 3 (SMS) - بدون تغییر -->
    <tr>
      <td>3</td>
      <td>—</td>
      <td>—</td>
      <td><code>EmailSender.java</code></td>
      <td>اضافه شدن <code>@Override</code> برای <code>sendSms(...)</code> (بدون پیاده‌سازی واقعی، چون SMS برای EmailSender در دسترس نیست).</td>
    </tr>

    <!-- ردیف 4 (Usage) - پیام قبلی بدون تغییر + پرداخت جدید اضافه شد -->
    <tr>
      <td>4</td>
      <td><code>Main / Usage</code></td>
      <td>
        برای استفاده از پرداخت حضوری، مقدار <code>PaymentMethods.ONSITE</code> را پاس دهید.
        حالت‌های قابل انتخاب: <code>PAYPAL</code>, <code>CARD</code>, <code>CASH</code>, <code>ONSITE</code>
        (حالت مدنظر: <code>ONSITE</code>)
      </td>
      <td><code>Main / Usage</code></td>
      <td>نمونه استفاده: <code>service.makeReservation(res, PaymentMethods.PAYPAL, Notifier.EMAIL);</code> (برای تست SMS می‌توانید <code>Notifier.SMS</code> بگذارید).</td>
    </tr>
  </tbody>
</table>
