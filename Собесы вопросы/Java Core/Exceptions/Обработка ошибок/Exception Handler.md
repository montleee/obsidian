для обработки `Exception` без `try catch`  используется `Exception Handler`

При `UserNotFoundException` обработает исключение, `return` 
- `404 HttpStatus`  
- `errorResponse`
```Java
@ControllerAdvice
public class GlobalExceptionHandler {
    // Обработка конкретного типа исключения
    @ExceptionHandler(UserNotFoundException.class)
    @ResponseStatus(HttpStatus.NOT_FOUND)
    public ResponseEntity<ErrorResponse> handleUserNotFoundException(UserNotFoundException ex) {
        var errorResponse = new ErrorResponse("USER_NOT_FOUND", ex.getMessage());
        return new ResponseEntity<>(errorResponse, HttpStatus.NOT_FOUND);
    }
}
```