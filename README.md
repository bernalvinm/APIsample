# API Test


You can run this using postman.
The code is run by Javascript.

const response = pm.response.json();
console.log(response.Name);
console.log(response.CanRelist);
console.log(response.Promotions[1]);
console.log(response.Promotions[1].Name);
console.log(response.Promotions[1].Description);

pm.test("Status code is 200", () => {
    pm.response.to.have.status(200);
});

pm.test("Name: Carbon credits is ok", () => {
    pm.expect(response.Name).to.eql("Carbon credits");
});

pm.test("CanRelist = True is ok", () => {
    pm.expect(response.CanRelist).to.be.true;
    pm.expect(response.CanRelist).to.eql(true);
});

pm.test("The Promotion Name Gallery with Description: Good position in category is ok", () => {
    pm.expect(response.Promotions[1].Name).to.eql("Gallery");
    pm.expect(response.Promotions[1].Description).to.eql("Good position in category");
});

/*
Another Code for Valdation

var response = JSON.parse(responseBody);
tests["Validating Status Code"] = responseCode.code == "200";
tests["Validating Name: Carbon Credits"] = response.Name == "Carbon credits";
tests["Validating CanRelist = true "] = response.CanRelist == true;
tests["Validating Name: Gallery"] = response.Promotions[1].Name == "Gallery";
tests["Validating Description: Good position in category"] = response.Promotions[1].Description == "Good position in category";
*/
