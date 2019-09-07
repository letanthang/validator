Validator lib return custom message (vi)

Golang, use lib validatorv9

#install  
go get github.com/letanthang/validator  
go get gopkg.in/go-playground/validator.v9  
go get github.com/go-playground/locales  
go get github.com/go-playground/universal-translator  

#usage - apply rule in struct  
type ContactRequest struct {  
	&nbsp;&nbsp;CustomerID int       `json:"customer_id,omitempty"`  
	&nbsp;&nbsp;Type       int       `json:"type" validate:"required"`  
	&nbsp;&nbsp;Fullname   string    `json:"fullname" validate:"required,min=5"`  
	&nbsp;&nbsp;Phone      string    `json:"phone" validate:"required,min=10,max=14"`  
	&nbsp;&nbsp;Email      string    `json:"email" validate:"required,email"`  
	&nbsp;&nbsp;Address    string    `json:"address" validate:"required"`  
	&nbsp;&nbsp;Location   []float64 `json:"location" validate:"required"`  
	&nbsp;&nbsp;RegionID   int       `json:"region_id" validate:"required"`  
	&nbsp;&nbsp;District   string    `json:"district" validate:"required"`  
	&nbsp;&nbsp;Province   string    `json:"province" validate:"required"`  
}  

#usage -- validate struct (in handler/model/..)  
if err := validator.Validate(objRequest); err != nil {  
  &nbsp;&nbsp;fmt.Println(err.Error())  
}
