# Python and Django

## Forms
label : 텍스트 클릭 시 해당 form에 연결

type  
- radio : 택1 옵션. name 값이 같으면 작동

```
<select name="">
    <option value=""></option>
</select>
```
스크롤 박스 생성.

textarea name="" rows="" cols=""  
rows : 보이는 줄 개수
cols : 글씨 수?

## Assessment

```
<!DOCTYPE html>
<html lang="en" dir="ltr">
  <head>
    <meta charset="utf-8">
    <title>Assessment Test HTML</title>
  </head>
  <body>
    <h1>Course Sign Up Page</h1>
    <p>
      Please Note: First Name, Last Name, Password, and Email are required
    </p>
    <form>
      <p>
        <label for="fn">First Name:</label>
        <input id="fn" type="text" name="fn" placeholder="First Name" required>
        <label for="ln">Last Name:</label>
        <input id="ln" type="text" name="ln" placeholder="Last Name" required></p>
      <p>
        <label for="em">Email:</label>
        <input id="em" type="email" name="em" placeholder="name@email.com" required>
        <label for="pw">Password:</label>
        <input id="pw" type="password" name="pw" required>
      </p>
      <p>
        Are you over the age of 18?
      </p>
      <p>
        <label for="yes">Yes:</label>
        <input id="yes" type="radio" name="age" value="yes">
        <label for="no">No:</label>
        <input id="no" type="radio" name="age" value="no">
      </p>
      <p>
        Do you have a Credit Card or PayPal?
      </p>
      <p>
        <select name="pay">
          <option value="1">Credit Card</option>
          <option value="2">PayPal</option>
        </select>
      </p>
      <p>
        <input type="submit" value="Sign Up">
      </p>
    </form>
  </body>
</html>
```