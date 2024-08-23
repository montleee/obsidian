```java
public interface PaymentService {
    void processPayment();
}
```
```java
@Service("creditCardPaymentService")
public class CreditCardPaymentService implements PaymentService {
    @Override
    public void processPayment() {
        System.out.println("Processing payment with Credit Card.");
    }
}
```
```java
@Service("paypalPaymentService")
public class PayPalPaymentService implements PaymentService {
    @Override
    public void processPayment() {
        System.out.println("Processing payment with PayPal.");
    }
}
```
```java
@Component
public class PaymentProcessor {

    private final PaymentService paymentService;

    @Autowired
    public PaymentProcessor(@Qualifier("creditCardPaymentService") PaymentService paymentService) {
        this.paymentService = paymentService;
    }
    public void process() {
        paymentService.processPayment();
    }
}

```