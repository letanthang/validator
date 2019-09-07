Validator lib return custom message (vi)

Golang, use lib validatorv9

#install
go get g.ghn.vn/logistic/validator
go get gopkg.in/go-playground/validator.v9
go get github.com/go-playground/locales
go get github.com/go-playground/universal-translator

#usage - apply rule in struct
type ContactRequest struct {
	CustomerID int       `json:"customer_id,omitempty"`
	Type       int       `json:"type" validate:"required"`
	Fullname   string    `json:"fullname" validate:"required,min=5"`
	Phone      string    `json:"phone" validate:"required,min=10,max=14"`
	Email      string    `json:"email" validate:"required,email"`
	Address    string    `json:"address" validate:"required"`
	Location   []float64 `json:"location" validate:"required"`
	RegionID   int       `json:"region_id" validate:"required"`
	District   string    `json:"district" validate:"required"`
	Province   string    `json:"province" validate:"required"`
}

#usage -- validate struct (in handler/model/..)
if err := validator.Validate(objRequest); err != nil {
  fmt.Println(err.Error())
}