# Web-page
This is my first repository
.formDiv {    
padding: 21px;    
 border-radius: 5px;    
 background-color: #f2f2f2;    
}    
    
input[type=text], select     
{    
  width: 100%;    
  padding: 12px 20px;    
  margin: 8px 0;    
  display: inline-block;    
  border: 1px solid #ccc;    
  border-radius: 4px;    
  box-sizing: border-box;    
}    
    
input[type=submit] {    
  width: 100%;    
  background-color: #4CAF50;    
  color: white;    
  padding: 14px 20px;    
  margin: 8px 0;    
  border: none;    
  border-radius: 4px;    
  cursor: pointer;    
}    
    input[type=submit]:hover {    
  background-color: #45a049;    
}    
.showError{    
  border-color: #a94442 !important;    
  color: #a94442 !important;    
  margin-bottom: 15px;    
}
import React, { Component } from "react";    
    
class AdmissionForm extends Component {    
    render() {    
        return (    
             
        )    
    }    
}     
export default AdmissionForm;
import React, { Component } from "react";    
import './AdmissionForm.css'      
class AdmissionForm extends Component {    
    constructor(props) {    
        super(props);    
        this.state = {    
            studName: '',    
            class: 'select',    
            dob: '',    
            gender: 'select',       
            division: 'select',    
            formErrors: {}    
        };    
        this.initialState = this.state;    
    }    
    handleFormValidation() {    
        const { studName, emailId, dob, gender, phoneNumber, city } = this.state;    
        let formErrors = {};    
        let formIsValid = true;    
        //Student name     
        if (!studName) {    
            formIsValid = false;    
            formErrors["studNameErr"] = "Name is required.";    
        }   
        //class 
         var pattern = /^(I \II \III\ IV \V\ V1\ V11\ V111\ 1X\ X\ X11\ X12)$/;
        if (class === '' || class === "select") {    
            formIsValid = false;    
            formErrors["classErr"] = "Select class.";    
        }    
        //DOB    
        if (!dob) {    
            formIsValid = false;    
            formErrors["dobErr"] = "Date of birth is required.";    
        }    
        else {    
            var pattern = /^(0[1-9]|1[0-9]|2[0-9]|3[0-1])\/(0[1-9]|1[0-2])\/([0-9]{4})$/;    
            if (!pattern.test(dob)) {    
                formIsValid = false;    
                formErrors["dobErr"] = "Invalid date of birth";    
            }    
        }    
         //Gender    
        if (gender === '' || gender === "select") {    
            formIsValid = false;    
            formErrors["genderErr"] = "Select gender.";    
        } 
        //division 
         var pattern = /^(A\B\C)$/;
        if (division === '' || division === "select") {    
            formIsValid = false;    
            formErrors["divisionErr"] = "Select division.";    
        }    
        this.setState({ formErrors: formErrors });    
        return formIsValid;    
    }    
    handleChange = (e) => {    
        const { name, value } = e.target;    
        this.setState({ [name]: value });    
    }   
    handleSubmit = (e) => {    
        e.preventDefault();    
        if (this.handleFormValidation()) {    
            alert('You have been successfully registered.')    
            this.setState(this.initialState)    
        }    
    }    
    render() {    
        const { studNameErr, classErr, dobErr, genderErr, divisionErr } = this.state.formErrors;    
        return (    
            <div className="formDiv">   
                <h3 style={{ textAlign: "center" }} >Student Admission Form </ h3>    
                <div>    
                    <form onSubmit={this.handleSubmit}>    
                        <div>    
                            <label htmlFor="studName">Name</label>    
                            <input type="text" name="studName"    
                                value={this.state.studName}    
                                onChange={this.handleChange}    
                                placeholder="Your name.."    
                                className={studNameErr ? ' showError' : ''} />    
                            {studNameErr &&    
                                <div style={{ color: "red", paddingBottom: 10 }}>{studNameErr}</div>    
                            }    
    
                        </div>    
                        <div>    
                            <label htmlFor="class"> Class</label>    
                            <input type="text" name="class"    
                                value={this.state.class}    
                                onChange={this.handleChange}    
                                placeholder="Your class.."    
                                className={classErr ? ' showError' : ''} > 
                          <option value="select">--Select--</option>    
                                <option value="I">I</option>    
                                <option value="II">II</option>    
                                <option value="III">III</option>  
                                <option value="IV">IV</option>    
                                <option value="V">V</option>    
                                <option value="V1">V1</option> 
                                <option value="V11">V11</option>    
                                <option value="V111">V111</option>    
                                <option value="1X">1X</option> 
                                <option value="X">X</option>    
                                <option value="X1">X1</option>    
                                <option value="X12">X12</option> 
                            </select>    
                            {classErr &&    
                                <div style={{ color: "red", paddingBottom: 10 }}>{classErr}</div>    
                            }    
    
                        </div>    
                        <div>    
                            <label htmlFor="text">Birth Date</label>    
                            <input type="text" name="dob"    
                                value={this.state.dob}    
                                onChange={this.handleChange}    
                                placeholder="DD/MM/YYYY.."    
                                className={dobErr ? ' showError' : ''} />    
                            {dobErr &&    
                                <div style={{ color: "red", paddingBottom: 10 }}>{dobErr}</div>    
                            }    
                        </div>    
                        <div>    
                            <label htmlFor="gender">Gender</label>    
                            <select name="gender" onChange={this.handleChange}    
                                className={genderErr ? ' showError' : ''}    
                                value={this.state.gender} >    
                                <option value="select">--Select--</option>    
                                <option value="male">Male</option>    
                                <option value="female">Female</option>    
                                <option value="female">Other</option>    
                            </select>    
                            {genderErr &&    
                                <div style={{ color: "red", paddingBottom: 10 }}>{genderErr}</div>    
                            }     
                        </div>    
                        <div>    
                            <label htmlFor="division">Division</label>    
                            <select name="division"    
                                value={this.state.division}    
                                onChange={this.handleChange}    
                                className={divisionErr ? ' showError' : ''} >    
                                <option value="select">--Select--</option>    
                                <option value="A">A</option>    
                                <option value="B">B</option>    
                                <option value="C">C</option>    
                            </select>    
                            {divisionErr &&    
                                <div style={{ color: "red", paddingBottom: 10 }}>{divisionErr}</div>    
                            }    
                        </div>    
                        <input type="submit" value="Submit" />    
                    </form>    
                </div>    
            </div >    
        )    
    }    
}    
    
export default AdmissionForm; 
import React, { Component } from 'react';    
import './App.css';    
import AdmissionForm from './AdmissionForm';    
    
export default class App extends Component {    
  render() {    
    return (    
      <div className="content">    
        <AdmissionForm />    
      </div >    
    );    
  }    
}
