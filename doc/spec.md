# MotionDeviceSystem

## Description

The MotionDeviceSystemType provides a representation of a motion device system as an entry point to
the OPC UA device set. At least one instance of a MotionDeviceSystemType must be instantiated in
the DeviceSet. This instance organises the information model of a complete robotics system using
instances of the described ObjectTypes. A motion device system may consist of multiple motion devices, controllers and safety systems.


## Data Model

The data model is defined as shown below:

-   `id` : Unique identifier.

-   `type` : Entity type. It must be equal to `MotionDeviceSystem`.

-   `Controllers` : Controllers is a container for one or more instances of the ControllerType. Controller represents a controlling unit of one or more motion devices. A controller can be e.g. a specific control cabinet or a PLC.

    -   Attribute type: Property. List of `ControllerType`.
    -   Optional

      -   `Components` : Components is a container for one or more instances of subtypes of ComponentType defined in OPC UA DI. The listed components are installed in the motion device system, e.g. a processing-unit, a power-supply, an IO-board or a drive, and have an electrical interface to the controller.

          -   Attribute type: Property. List of `ComponentType`.
          -   Optional

      -   `Manufacturer` : The name of the company that manufactured the device.

          -   Attribute type: Property. [Text](https://schema.org/Text)
          -   Mandatory

      -   `Model` : The name of the product.

          -   Attribute type: Property. [Text](https://schema.org/Text)
          -   Mandatory

      -   `ParameterSet` : Provides a set of parameters.

          -   Attribute type: Property. [StructuredValue](https://schema.org/StructuredValue)
          -   Optional

              -   `CPUFanSpeed` : The speed of the CPU fan.

                  -   Attribute type: Property. [Number](https://schema.org/Number)
                  -   Optional

              -   `CabinetFanSpeed` : The speed of the cabinet fan.

                  -   Attribute type: Property. [Number](https://schema.org/Number)
                  -   Optional

              -   `InputVoltage` : The input voltage of the controller which can be a configured value. To distinguish between an AC or DC supply the optional property Definition of the base type DataItemType shall be used.

                  -   Attribute type: Property. [Number](https://schema.org/Number)
                  -   Optional

              -   `StartUpTime` : The date and time of the last start-up of the controller.

                  -   Attribute type: Property. [DateTime](https://schema.org/DateTime)
                  -   Optional

              -   `Temperature` : The controller temperature given by a temperature sensor inside of the controller.

                  -   Attribute type: Property. [Number](https://schema.org/Number)
                  -   Optional

              -   `TotalEnergyConsumption` : The otal accumulated energy consumed by the motion devices related with this controller instance.

                  -   Attribute type: Property. [Number](https://schema.org/Number)
                  -   Optional

              -   `TotalPowerOnTime` : The total accumulated time the controller was powered on.

                  -   Attribute type: Property. [Text](https://schema.org/Text)
                  -   Optional

              -   `UPSState` : The vendor specific status of an integrated uninterruptible power supply or accumulator system.

                  -   Attribute type: Property. [Text](https://schema.org/Text)
                  -   Optional

      -   `ProductCode` : A unique combination of numbers and letters used to identify the product. It may be the order information displayed on type shields or in ERP systems.

          -   Attribute type: Property. [Text](https://schema.org/Text)
          -   Mandatory

      -   `SerialNumber` : A unique production number assigned by the manufacturer of the device. This is often stamped on the outside of the device and may be used for traceability and warranty purposes.

          -   Attribute type: Property. [Text](https://schema.org/Text)
          -   Mandatory

      -   `Software` : Software is a container for one or more instances of SoftwareType defined in OPC UA DI. Each controller has at least one software installed that is a runtime software or firmware of the controller. NOTE This type of program is usually generated before installation and can only be modified thereafter by the manufacturer.

          -   Attribute type: Property.  List of `SoftwareType`
          -   Mandatory

      -   `TaskControls` : TaskControls is a container for one or more instances of TaskControlType. The task control describes an execution engine that loads and runs task programs. One task runs one task program at the time. The system should instantiate the maximum allowed number of task controls.

          -   Attribute type: Property.  List of `TaskControlType`
          -   Optional

          -   `ParameterSet` : Provides a set of parameters.

              -   Attribute type: Property. [StructuredValue](https://schema.org/StructuredValue)
              -   Optional

                  -   `TaskProgramName` : A customer given identifier for the task program.

                      -   Attribute type: Property. [Text](https://schema.org/Text)
                      -   Mandatory

                  -   `TaskProgramLoaded` : TRUE if a task program is loaded in the task control, FALSE otherwise.

                      -   Attribute type: Property. [Boolean](https://schema.org/Boolean)
                      -   Mandatory

                  -   `ExecutionMode` : How the task control executes the task program.

                      -   Attribute type: Property. [Number](https://schema.org/Number)
                      -   Mandatory


-   `MotionDevices` : MotionDevices is a container for one or more instances of the MotionDeviceType.  A motion device has as least one axis and is a multifunctional manipulator designed to move material, parts, tools or specialized devices through variable programmed motions for the performance of a variety of tasks. Examples are an industrial robot, positioner or mobile platform.

    -   Attribute type: Property. List of `MotionDeviceType`.
    -   Optional

      -   `AdditionalComponents` : AdditionalComponents is a container for one or more instances of subtypes of ComponentType defined in OPC UA DI. The listed components are installed at the motion device, e.g. an IO-board.

          -   Attribute type: Property.  List of `AdditionalComponent`.
          -   Optional

      -   `Axes` : Axes is a container for one or more instances of the AxisType.

          -   Attribute type: Property.  List of `AxisType`.
          -   Optional

              -   `MotionProfile` : The kind of axis motion as defined by the AxisMotionProfileEnumeration.

                  -   Attribute type: Property.   [Number](https://schema.org/Number)
                  -   Optional

                      -   `ParameterSet` : Provides a set of parameters.

                          -   Attribute type: Property. [StructuredValue](https://schema.org/StructuredValue)
                          -   Optional

                              -   `ActualPosition` : The current position of the axis.

                                  -   Attribute type: Property. [Number](https://schema.org/Number)
                                  -   Mandatory

                              -   `ActualSpeed` : The axis speed.

                                  -   Attribute type: Property. [Number](https://schema.org/Number)
                                  -   Optional

                              -   `ActualAcceleration` : The axis acceleration.

                                  -   Attribute type: Property. [Number](https://schema.org/Number)
                                  -   Optional

                          -   `Manufacturer` : The name of the company that manufactured the device.

                              -   Attribute type: Property. [Text](https://schema.org/Text)
                              -   Mandatory

                          -   `Model` : The name of the product.

                              -   Attribute type: Property. [Text](https://schema.org/Text)
                              -   Mandatory

                          -   `MotionDeviceCategoryEnumeration` : The kind of motion device defined by MotionDeviceCategoryEnumeration based on ISO 8373.

                              -   Attribute type: Property.  [Number](https://schema.org/Number)
                              -   Mandatory

                          -   `ParameterSet` : Provides a set of parameters.

                              -   Attribute type: Property. [StructuredValue](https://schema.org/StructuredValue)
                              -   Optional

                                  -   `InControl` : The information if the actuators (in most cases a motor) of the motion device are powered up and in control: "true".

                                      -   Attribute type: Property. [Number](https://schema.org/Number)
                                      -   Optional

                                  -   `OnPath` : True if the motion device is on or near enough the planned program path such that program execution can continue. If the MotionDevice deviates too much from this path in case of errors or an emergency stop, this value becomes false. If OnPath is false, the motion device needs repositioning to continue program execution.

                                      -   Attribute type: Property. [Number](https://schema.org/Number)
                                      -   Optional

                                  -   `SpeedOverride` : The current speed setting in percent of programmed speed (0 - 100%).

                                      -   Attribute type: Property. [Number](https://schema.org/Number)
                                      -   Mandatory

                          -   `PowerTrains` : PowerTrains is a container for one or more instances of the PowerTrainType.

                              -   Attribute type: Property. List of `PowerTrainType`.
                              -   Mandatory

                                  -   `Gears` : Gears is a container for one or more instances of the GearType.

                                      -   Attribute type: Property. List of `GearType`.
                                      -   Mandatory

                                          -   `GearRatio` : The transmission ratio of the gear expressed as a fraction as input velocity (motor side) by output velocity (load side).

                                              -   Attribute type: Property. [Number](https://schema.org/Number)
                                              -   Mandatory

                                          -   `Manufacturer` : The name of the company that manufactured the device.

                                              -   Attribute type: Property. [Text](https://schema.org/Text)
                                              -   Mandatory

                                          -   `Model` : The name of the product.

                                              -   Attribute type: Property. [Text](https://schema.org/Text)
                                              -   Mandatory

                                          -   `Pitch` : The distance covered in millimeters (mm) for linear motion per one revolution of the output side of the driving unit. Pitch is used in combination with GearRatio to describe the overall transmission from input to output of the gear.

                                              -   Attribute type: Property. [Number](https://schema.org/Number)
                                              -   Mandatory

                                          -   `ProductCode` : A unique combination of numbers and letters used to identify the product. It may be the order information displayed on type shields or in ERP systems.

                                              -   Attribute type: Property. [Text](https://schema.org/Text)
                                              -   Mandatory

                                          -   `SerialNumber` : A unique production number assigned by the manufacturer of the device. This is often stamped on the outside of the device and may be used for traceability and warranty purposes.

                                              -   Attribute type: Property. [Text](https://schema.org/Text)
                                              -   Mandatory

                                  -   `Motors` : Motors is a container for one or more instances of the MotorType.

                                      -   Attribute type: Property. List of `MotorType`.
                                      -   Mandatory

                                          -   `Manufacturer` : The name of the company that manufactured the device.

                                              -   Attribute type: Property. [Text](https://schema.org/Text)
                                              -   Mandatory

                                          -   `Model` : The name of the product.

                                              -   Attribute type: Property. [Text](https://schema.org/Text)
                                              -   Mandatory

                                          -   `ParameterSet` : Provides a set of parameters.

                                              -   Attribute type: Property. [StructuredValue](https://schema.org/StructuredValue)
                                              -   Optional

                                                  -   `BrakeReleased:` : TRUE the motor is free to run. FALSE means that the motor shaft is locked by the brake.

                                                      -   Attribute type: Property. [Boolean](https://schema.org/Boolean)
                                                      -   Optional

                                                  -   `MotorTemperature:` : The temperature of the motor.

                                                      -   Attribute type: Property. [Number](https://schema.org/Number)
                                                      -   Mandatory

                                                  -   `EffectiveLoadRate` : A percentage of maximum continuous load.

                                                      -   Attribute type: Property. [Number](https://schema.org/Number)
                                                      -   Optional

                                          -   `ProductCode` : A unique combination of numbers and letters used to identify the product. It may be the order information displayed on type shields or in ERP systems.

                                              -   Attribute type: Property. [Text](https://schema.org/Text)
                                              -   Mandatory

                                          -   `SerialNumber` : A unique production number assigned by the manufacturer of the device. This is often stamped on the outside of the device and may be used for traceability and warranty purposes.

                                              -   Attribute type: Property. [Text](https://schema.org/Text)
                                              -   Mandatory

                          -   `ProductCode` : A unique combination of numbers and letters used to identify the product. It may be the order information displayed on type shields or in ERP systems.

                              -   Attribute type: Property. [Text](https://schema.org/Text)
                              -   Mandatory

                          -   `SerialNumber` : A unique production number assigned by the manufacturer of the device. This is often stamped on the outside of the device and may be used for traceability and warranty purposes.

                              -   Attribute type: Property. [Text](https://schema.org/Text)
                              -   Mandatory

-   `SafetyStates`: SafetyStates is a container for one or more instances of the SafetyStatesType.

    -   Attribute type: Property. List of `SafetyStatesType`.
    -   Optional

        -   `EmergencyStopFunctions` : EmergencyStopFunctions is a container for one or more instances of the EmergencyStopFunctionType. The number and names of emergency stop functions is vendor specific.

            -   Attribute type: Property. List of `EmergencyStopFunctionType`.
            -   Optional

            -   `Active:` : TRUE if this particular emergency stop function is active, e.g. that the emergency stop button is pressed, FALSE otherwise.

                -   Attribute type: Property. [Boolean](https://schema.org/Boolean)
                -   Mandatory

            -   `Name:` : Manufacturer-specific emergency stop function identifier within the safety system.

                -   Attribute type: Property. [Text](https://schema.org/Text)
                -   Mandatory

        -   `ParameterSet` : Provides a set of parameters.

            -   Attribute type: Property. [StructuredValue](https://schema.org/StructuredValue)
            -   Optional

                -   `EmergencyStop:` : TRUE if one or more of the emergency stop functions in the robot system are active, FALSE otherwise. If the EmergencyStopFunctions object is provided, then the value of this variable is TRUE if one or more of the listed emergency stop functions are active.

                    -   Attribute type: Property. [Boolean](https://schema.org/Boolean)
                    -   Mandatory

                -   `OperationalMode:` : The current operational mode. Allowed values are described in OperationalModeEnumeration, see ISO 10218-1:2011.

                    -   Attribute type: Property. [Number](https://schema.org/Number)
                    -   Mandatory

                -   `ProtectiveStop` : TRUE if one or more of the enabled protective stop functions in the system are active, FALSE otherwise. If the ProtectiveStopFunctions object is provided, then the value of this variable is TRUE if one or more of the listed protective stop functions are enabled and active.

                    -   Attribute type: Property. [Boolean](https://schema.org/Boolean)
                    -   Mandatory

        -   `ProtectiveStopFunctions` : ProtectiveStopFunctions is a container for one or more instances of the ProtectiveStopFunctionType. The number and names of protective stop functions is vendor specific.

            -   Attribute type: Property. List of `EmergencyStopFunctionType`.
            -   Optional

                -   `Active:` : TRUE if this particular protective stop function is active, e.g. that a stop is initiated, FALSE otherwise. If Enabled is FALSE then Active shall be FALSE.

                    -   Attribute type: Property. [Boolean](https://schema.org/Boolean)
                    -   Mandatory

                -   `Enabled:` : TRUE if this protective stop function is currently supervising the system, FALSE otherwise. A protective stop function may or may not be enabled at all times, e.g. the protective stop function of the safety doors are typically enabled in automatic operational mode and disabled in manual mode. On the other hand for example, the protective stop function of the teach pendant enabling device is enabled in manual modes and disabled in automatic modes.

                    -   Attribute type: Property. [Boolean](https://schema.org/Boolean)
                    -   Mandatory

                -   `Name:` : Manufacturer-specific protective stop function identifier within the safety system.

                    -   Attribute type: Property. [Text](https://schema.org/Text)
                    -   Mandatory

**Note**: JSON Schemas are intended to capture the data type and associated
constraints of the different Attributes, regardless their final representation
format in NGSI(v2, LD).

## Examples

### Normalized Example

Normalized NGSI response

```json
{
	"id": "MyMotionDeviceSystem",
	"type": "MotionDeviceSystem",
	"Controllers": {
		"type": "StructuredValue",
		"value": [{
			"type": "StructuredValue",
			"value": [{
					"type": "LocalizedText",
					"value": "Engineering Ingegneria Informatica",
					"metadata": {
						"BrowseName": {
							"type": "String",
							"value": "NAMESPACEINDEX:Manufacturer"
						},
						"NodeId": {
							"type": "String",
							"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
						}
					}
				},
				{
					"type": "LocalizedText",
					"value": "Model",
					"metadata": {
						"BrowseName": {
							"type": "String",
							"value": "NAMESPACEINDEX:Model"
						},
						"NodeId": {
							"type": "String",
							"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
						}
					}
				},
				{
					"type": "String",
					"value": "MP695ENG004",
					"metadata": {
						"BrowseName": {
							"type": "String",
							"value": "NAMESPACEINDEX:ProductCode"
						},
						"NodeId": {
							"type": "String",
							"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
						}
					}
				},
				{
					"type": "String",
					"value": "ENG-004",
					"metadata": {
						"BrowseName": {
							"type": "String",
							"value": "NAMESPACEINDEX:SerialNumber"
						},
						"NodeId": {
							"type": "String",
							"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
						}
					}
				},
				{
					"type": "StructuredValue",
					"value": [{
							"type": "Double",
							"value": 1600.0,
							"metadata": {
								"BrowseName": {
									"type": "String",
									"value": "NAMESPACEINDEX:CPUFanSpeed"
								},
								"NodeId": {
									"type": "String",
									"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
								}
							}
						},
						{
							"type": "Double",
							"value": 2000.5,
							"metadata": {
								"BrowseName": {
									"type": "String",
									"value": "NAMESPACEINDEX:CabinetFanSpeed"
								},
								"NodeId": {
									"type": "String",
									"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
								}
							}
						},
						{
							"type": "Double",
							"value": 2500.0,
							"metadata": {
								"BrowseName": {
									"type": "String",
									"value": "NAMESPACEINDEX:InputVoltage"
								},
								"NodeId": {
									"type": "String",
									"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
								}
							}
						},
						{
							"type": "DateTime",
							"value": "2020-10-19T07:36:06.713Z",
							"metadata": {
								"BrowseName": {
									"type": "String",
									"value": "NAMESPACEINDEX:StartUpTime"
								},
								"NodeId": {
									"type": "String",
									"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
								}
							}
						},
						{
							"type": "Double",
							"value": 50.0,
							"metadata": {
								"BrowseName": {
									"type": "String",
									"value": "NAMESPACEINDEX:Temperature"
								},
								"NodeId": {
									"type": "String",
									"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
								}
							}
						},
						{
							"type": "Double",
							"value": 170.1,
							"metadata": {
								"BrowseName": {
									"type": "String",
									"value": "NAMESPACEINDEX:TotalEnergyConsumption"
								},
								"NodeId": {
									"type": "String",
									"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
								}
							}
						},
						{
							"type": "DurationString",
							"value": "",
							"metadata": {
								"BrowseName": {
									"type": "String",
									"value": "NAMESPACEINDEX:TotalPowerOnTime"
								},
								"NodeId": {
									"type": "String",
									"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
								}
							}
						},
						{
							"type": "String",
							"value": "alive",
							"metadata": {
								"BrowseName": {
									"type": "String",
									"value": "NAMESPACEINDEX:UPSState"
								},
								"NodeId": {
									"type": "String",
									"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
								}
							}
						}
					],
					"metadata": {
						"BrowseName": {
							"type": "String",
							"value": "NAMESPACEINDEX:ParameterSet"
						},
						"NodeId": {
							"type": "String",
							"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
						}
					}
				},
				{
					"type": "StructuredValue",
					"value": [{
						"type": "StructuredValue",
						"value": {

						},
						"metadata": {
							"BrowseName": {
								"type": "String",
								"value": "NAMESPACEINDEX:Component"
							},
							"NodeId": {
								"type": "String",
								"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
							}
						}
					}],
					"metadata": {
						"BrowseName": {
							"type": "String",
							"value": "NAMESPACEINDEX:Components"
						},
						"NodeId": {
							"type": "String",
							"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
						}
					}
				},
				{
					"type": "StructuredValue",
					"value": [

					],
					"metadata": {
						"BrowseName": {
							"type": "String",
							"value": "NAMESPACEINDEX:Software"
						},
						"NodeId": {
							"type": "String",
							"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
						}
					}
				},
				{
					"type": "StructuredValue",
					"value": [{
						"type": "StructuredValue",
						"value": [{
							"type": "StructuredValue",
							"value": [{
									"type": "String",
									"value": "TaskProg",
									"metadata": {
										"BrowseName": {
											"type": "String",
											"value": "NAMESPACEINDEX:TaskProgramName"
										},
										"NodeId": {
											"type": "String",
											"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
										}
									}
								},
								{
									"type": "Boolean",
									"value": true,
									"metadata": {
										"BrowseName": {
											"type": "String",
											"value": "NAMESPACEINDEX:TaskProgramLoaded"
										},
										"NodeId": {
											"type": "String",
											"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
										}
									}
								},
								{
									"type": "Integer",
									"value": 0,
									"metadata": {
										"BrowseName": {
											"type": "String",
											"value": "NAMESPACEINDEX:ExecutionMode"
										},
										"NodeId": {
											"type": "String",
											"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
										}
									}
								}
							],
							"metadata": {
								"BrowseName": {
									"type": "String",
									"value": "NAMESPACEINDEX:ParameterSet"
								},
								"NodeId": {
									"type": "String",
									"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
								}
							}
						}],
						"metadata": {
							"BrowseName": {
								"type": "String",
								"value": "NAMESPACEINDEX:TaskControl"
							},
							"NodeId": {
								"type": "String",
								"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
							}
						}
					}],
					"metadata": {
						"BrowseName": {
							"type": "String",
							"value": "NAMESPACEINDEX:TaskControls"
						},
						"NodeId": {
							"type": "String",
							"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
						}
					}
				}
			],
			"metadata": {
				"BrowseName": {
					"type": "String",
					"value": "NAMESPACEINDEX:Controller"
				},
				"NodeId": {
					"type": "String",
					"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
				}
			}
		}],
		"metadata": {
			"BrowseName": {
				"type": "String",
				"value": "NAMESPACEINDEX:Controllers"
			},
			"NodeId": {
				"type": "String",
				"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
			}
		}
	},
	"MotionDevices": {
		"type": "StructuredValue",
		"value": [{
			"type": "StructuredValue",
			"value": [{
					"type": "LocalizedText",
					"value": "Engineering Ingegneria Informatica",
					"metadata": {
						"BrowseName": {
							"type": "String",
							"value": "NAMESPACEINDEX:Manufacturer"
						},
						"NodeId": {
							"type": "String",
							"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
						}
					}
				},
				{
					"type": "LocalizedText",
					"value": "Model",
					"metadata": {
						"BrowseName": {
							"type": "String",
							"value": "NAMESPACEINDEX:Model"
						},
						"NodeId": {
							"type": "String",
							"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
						}
					}
				},
				{
					"type": "String",
					"value": "MP695ENG004",
					"metadata": {
						"BrowseName": {
							"type": "String",
							"value": "NAMESPACEINDEX:ProductCode"
						},
						"NodeId": {
							"type": "String",
							"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
						}
					}
				},
				{
					"type": "String",
					"value": "ENG-004",
					"metadata": {
						"BrowseName": {
							"type": "String",
							"value": "NAMESPACEINDEX:SerialNumber"
						},
						"NodeId": {
							"type": "String",
							"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
						}
					}
				},
				{
					"type": "Integer",
					"value": 0,
					"metadata": {
						"BrowseName": {
							"type": "String",
							"value": "NAMESPACEINDEX:MotionDeviceCategory"
						},
						"NodeId": {
							"type": "String",
							"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
						}
					}
				},
				{
					"type": "StructuredValue",
					"value": [{
						"type": "StructuredValue",
						"value": {},
						"metadata": {
							"BrowseName": {
								"type": "String",
								"value": "NAMESPACEINDEX:AdditionalComponent"
							},
							"NodeId": {
								"type": "String",
								"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
							}
						}
					}],
					"metadata": {
						"BrowseName": {
							"type": "String",
							"value": "NAMESPACEINDEX:AdditionalComponents"
						},
						"NodeId": {
							"type": "String",
							"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
						}
					}
				},
				{
					"type": "StructuredValue",
					"value": [{
							"type": "StructuredValue",
							"value": [{
									"type": "Integer",
									"value": 0,
									"metadata": {
										"BrowseName": {
											"type": "String",
											"value": "NAMESPACEINDEX:MotionProfile"
										},
										"NodeId": {
											"type": "String",
											"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
										}
									}
								},
								{
									"type": "StructuredValue",
									"value": [{
											"type": "Double",
											"value": 15.0,
											"metadata": {
												"BrowseName": {
													"type": "String",
													"value": "NAMESPACEINDEX:ActualPosition"
												},
												"NodeId": {
													"type": "String",
													"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
												}
											}
										},
										{
											"type": "Double",
											"value": 1.0,
											"metadata": {
												"BrowseName": {
													"type": "String",
													"value": "NAMESPACEINDEX:ActualSpeed"
												},
												"NodeId": {
													"type": "String",
													"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
												}
											}
										},
										{
											"type": "Double",
											"value": 0.5,
											"metadata": {
												"BrowseName": {
													"type": "String",
													"value": "NAMESPACEINDEX:ActualAcceleration"
												},
												"NodeId": {
													"type": "String",
													"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
												}
											}
										}
									],
									"metadata": {
										"BrowseName": {
											"type": "String",
											"value": "NAMESPACEINDEX:ParameterSet"
										},
										"NodeId": {
											"type": "String",
											"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
										}
									}
								}
							],
							"metadata": {
								"BrowseName": {
									"type": "String",
									"value": "NAMESPACEINDEX:AxisX"
								},
								"NodeId": {
									"type": "String",
									"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
								}
							}
						},
						{
							"type": "StructuredValue",
							"value": [{
									"type": "Integer",
									"value": 0,
									"metadata": {
										"BrowseName": {
											"type": "String",
											"value": "NAMESPACEINDEX:MotionProfile"
										},
										"NodeId": {
											"type": "String",
											"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
										}
									}
								},
								{
									"type": "StructuredValue",
									"value": [{
											"type": "Double",
											"value": 15.0,
											"metadata": {
												"BrowseName": {
													"type": "String",
													"value": "NAMESPACEINDEX:ActualPosition"
												},
												"NodeId": {
													"type": "String",
													"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
												}
											}
										},
										{
											"type": "Double",
											"value": 1.0,
											"metadata": {
												"BrowseName": {
													"type": "String",
													"value": "NAMESPACEINDEX:ActualSpeed"
												},
												"NodeId": {
													"type": "String",
													"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
												}
											}
										},
										{
											"type": "Double",
											"value": 0.5,
											"metadata": {
												"BrowseName": {
													"type": "String",
													"value": "NAMESPACEINDEX:ActualAcceleration"
												},
												"NodeId": {
													"type": "String",
													"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
												}
											}
										}
									],
									"metadata": {
										"BrowseName": {
											"type": "String",
											"value": "NAMESPACEINDEX:ParameterSet"
										},
										"NodeId": {
											"type": "String",
											"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
										}
									}
								}
							],
							"metadata": {
								"BrowseName": {
									"type": "String",
									"value": "NAMESPACEINDEX:AxisY"
								},
								"NodeId": {
									"type": "String",
									"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
								}
							}
						}
					],
					"metadata": {
						"BrowseName": {
							"type": "String",
							"value": "NAMESPACEINDEX:Axes"
						},
						"NodeId": {
							"type": "String",
							"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
						}
					}
				},
				{
					"type": "StructuredValue",
					"value": [{
							"type": "Boolean",
							"value": true,
							"metadata": {
								"BrowseName": {
									"type": "String",
									"value": "NAMESPACEINDEX:OnPath"
								},
								"NodeId": {
									"type": "String",
									"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
								}
							}
						},
						{
							"type": "Boolean",
							"value": true,
							"metadata": {
								"BrowseName": {
									"type": "String",
									"value": "NAMESPACEINDEX:InControl"
								},
								"NodeId": {
									"type": "String",
									"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
								}
							}
						},
						{
							"type": "Double",
							"value": 0.5,
							"metadata": {
								"BrowseName": {
									"type": "String",
									"value": "NAMESPACEINDEX:SpeedOverride"
								},
								"NodeId": {
									"type": "String",
									"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
								}
							}
						}
					],
					"metadata": {
						"BrowseName": {
							"type": "String",
							"value": "NAMESPACEINDEX:ParameterSet"
						},
						"NodeId": {
							"type": "String",
							"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
						}
					}
				},
				{
					"type": "StructuredValue",
					"value": [{
						"type": "StructuredValue",
						"value": [{
								"type": "StructuredValue",
								"value": [{
									"type": "StructuredValue",
									"value": [{
											"type": "LocalizedText",
											"value": "Engineering Ingegneria Informatica",
											"metadata": {
												"BrowseName": {
													"type": "String",
													"value": "NAMESPACEINDEX:Manufacturer"
												},
												"NodeId": {
													"type": "String",
													"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
												}
											}
										},
										{
											"type": "LocalizedText",
											"value": "Model",
											"metadata": {
												"BrowseName": {
													"type": "String",
													"value": "NAMESPACEINDEX:Model"
												},
												"NodeId": {
													"type": "String",
													"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
												}
											}
										},
										{
											"type": "String",
											"value": "MP695ENG003",
											"metadata": {
												"BrowseName": {
													"type": "String",
													"value": "NAMESPACEINDEX:ProductCode"
												},
												"NodeId": {
													"type": "String",
													"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
												}
											}
										},
										{
											"type": "String",
											"value": "ENG-003",
											"metadata": {
												"BrowseName": {
													"type": "String",
													"value": "NAMESPACEINDEX:SerialNumber"
												},
												"NodeId": {
													"type": "String",
													"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
												}
											}
										},
										{
											"type": "Double",
											"value": "0.25",
											"metadata": {
												"BrowseName": {
													"type": "String",
													"value": "NAMESPACEINDEX:GearRatio"
												},
												"NodeId": {
													"type": "String",
													"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
												}
											}
										},
										{
											"type": "Double",
											"value": "1.5",
											"metadata": {
												"BrowseName": {
													"type": "String",
													"value": "NAMESPACEINDEX:Pitch"
												},
												"NodeId": {
													"type": "String",
													"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
												}
											}
										}
									],
									"metadata": {
										"BrowseName": {
											"type": "String",
											"value": "NAMESPACEINDEX:Gear"
										},
										"NodeId": {
											"type": "String",
											"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
										}
									}
								}],
								"metadata": {
									"BrowseName": {
										"type": "String",
										"value": "NAMESPACEINDEX:Gears"
									},
									"NodeId": {
										"type": "String",
										"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
									}
								}
							},
							{
								"type": "StructuredValue",
								"value": [{
									"type": "StructuredValue",
									"value": [{
											"type": "LocalizedText",
											"value": "Engineering Ingegneria Informatica",
											"metadata": {
												"BrowseName": {
													"type": "String",
													"value": "NAMESPACEINDEX:Manufacturer"
												},
												"NodeId": {
													"type": "String",
													"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
												}
											}
										},
										{
											"type": "LocalizedText",
											"value": "Model",
											"metadata": {
												"BrowseName": {
													"type": "String",
													"value": "NAMESPACEINDEX:Model"
												},
												"NodeId": {
													"type": "String",
													"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
												}
											}
										},
										{
											"type": "String",
											"value": "MP695ENG002",
											"metadata": {
												"BrowseName": {
													"type": "String",
													"value": "NAMESPACEINDEX:ProductCode"
												},
												"NodeId": {
													"type": "String",
													"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
												}
											}
										},
										{
											"type": "String",
											"value": "ENG-002",
											"metadata": {
												"BrowseName": {
													"type": "String",
													"value": "NAMESPACEINDEX:SerialNumber"
												},
												"NodeId": {
													"type": "String",
													"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
												}
											}
										},
										{
											"type": "StructuredValue",
											"value": [{
													"type": "Boolean",
													"value": true,
													"metadata": {
														"BrowseName": {
															"type": "String",
															"value": "NAMESPACEINDEX:BrakeReleased"
														},
														"NodeId": {
															"type": "String",
															"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
														}
													}
												},
												{
													"type": "Double",
													"value": 75.0,
													"metadata": {
														"BrowseName": {
															"type": "String",
															"value": "NAMESPACEINDEX:motorTemperature"
														},
														"NodeId": {
															"type": "String",
															"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
														}
													}
												},
												{
													"type": "Integer",
													"value": 0,
													"metadata": {
														"BrowseName": {
															"type": "String",
															"value": "NAMESPACEINDEX:EffectiveLoadRate"
														},
														"NodeId": {
															"type": "String",
															"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
														}
													}
												}
											],
											"metadata": {
												"BrowseName": {
													"type": "String",
													"value": "NAMESPACEINDEX:ParameterSet"
												},
												"NodeId": {
													"type": "String",
													"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
												}
											}
										}
									],
									"metadata": {
										"BrowseName": {
											"type": "String",
											"value": "NAMESPACEINDEX:Motor"
										},
										"NodeId": {
											"type": "String",
											"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
										}
									}
								}],
								"metadata": {
									"BrowseName": {
										"type": "String",
										"value": "NAMESPACEINDEX:Motors"
									},
									"NodeId": {
										"type": "String",
										"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
									}
								}
							}
						],
						"metadata": {
							"BrowseName": {
								"type": "String",
								"value": "NAMESPACEINDEX:PowerTrain"
							},
							"NodeId": {
								"type": "String",
								"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
							}
						}
					}],
					"metadata": {
						"BrowseName": {
							"type": "String",
							"value": "NAMESPACEINDEX:PowerTrains"
						},
						"NodeId": {
							"type": "String",
							"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
						}
					}
				}
			],
			"metadata": {
				"BrowseName": {
					"type": "String",
					"value": "NAMESPACEINDEX:MotionDevice"
				},
				"NodeId": {
					"type": "String",
					"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
				}
			}
		}],
		"metadata": {
			"BrowseName": {
				"type": "String",
				"value": "NAMESPACEINDEX:MotionDevices"
			},
			"NodeId": {
				"type": "String",
				"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
			}
		}
	},
	"SafetyStates": {
		"type": "StructuredValue",
		"value": [{
			"type": "StructuredValue",
			"value": [{
					"type": "StructuredValue",
					"value": [{
							"type": "Integer",
							"value": 0,
							"metadata": {
								"BrowseName": {
									"type": "String",
									"value": "NAMESPACEINDEX:OperationalMode"
								},
								"NodeId": {
									"type": "String",
									"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
								}
							}
						},
						{
							"type": "Boolean",
							"value": true,
							"metadata": {
								"BrowseName": {
									"type": "String",
									"value": "NAMESPACEINDEX:ProtectiveStop"
								},
								"NodeId": {
									"type": "String",
									"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
								}
							}
						},
						{
							"type": "Boolean",
							"value": true,
							"metadata": {
								"BrowseName": {
									"type": "String",
									"value": "NAMESPACEINDEX:EmergencyStop"
								},
								"NodeId": {
									"type": "String",
									"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
								}
							}
						}
					],
					"metadata": {
						"BrowseName": {
							"type": "String",
							"value": "NAMESPACEINDEX:ParameterSet"
						},
						"NodeId": {
							"type": "String",
							"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
						}
					}
				},
				{
					"type": "StructuredValue",
					"value": [{
						"type": "StructuredValue",
						"value": [{
								"type": "String",
								"value": "EmergencyStopFunc",
								"metadata": {
									"BrowseName": {
										"type": "String",
										"value": "NAMESPACEINDEX:name"
									},
									"NodeId": {
										"type": "String",
										"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
									}
								}
							},
							{
								"type": "Boolean",
								"value": true,
								"metadata": {
									"BrowseName": {
										"type": "String",
										"value": "NAMESPACEINDEX:Active"
									},
									"NodeId": {
										"type": "String",
										"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
									}
								}
							}
						],
						"metadata": {
							"BrowseName": {
								"type": "String",
								"value": "NAMESPACEINDEX:EmergencyStopFunction"
							},
							"NodeId": {
								"type": "String",
								"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
							}
						}
					}],
					"metadata": {
						"BrowseName": {
							"type": "String",
							"value": "NAMESPACEINDEX:EmergencyStopFunctions"
						},
						"NodeId": {
							"type": "String",
							"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
						}
					}
				},
				{
					"type": "StructuredValue",
					"value": [{
						"type": "StructuredValue",
						"value": [{
								"type": "String",
								"value": "ProtectiveStopFunc",
								"metadata": {
									"BrowseName": {
										"type": "String",
										"value": "NAMESPACEINDEX:name"
									},
									"NodeId": {
										"type": "String",
										"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
									}
								}
							},
							{
								"type": "Boolean",
								"value": true,
								"metadata": {
									"BrowseName": {
										"type": "String",
										"value": "NAMESPACEINDEX:Active"
									},
									"NodeId": {
										"type": "String",
										"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
									}
								}
							},
							{
								"type": "Boolean",
								"value": true,
								"metadata": {
									"BrowseName": {
										"type": "String",
										"value": "NAMESPACEINDEX:Enabled"
									},
									"NodeId": {
										"type": "String",
										"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
									}
								}
							}
						],
						"metadata": {
							"BrowseName": {
								"type": "String",
								"value": "NAMESPACEINDEX:ProtectiveStopFunction"
							},
							"NodeId": {
								"type": "String",
								"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
							}
						}
					}],
					"metadata": {
						"BrowseName": {
							"type": "String",
							"value": "NAMESPACEINDEX:ProtectiveStopFunctions"
						},
						"NodeId": {
							"type": "String",
							"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
						}
					}
				}
			],
			"metadata": {
				"BrowseName": {
					"type": "String",
					"value": "NAMESPACEINDEX:SafetyState"
				},
				"NodeId": {
					"type": "String",
					"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
				}
			}
		}],
		"metadata": {
			"BrowseName": {
				"type": "String",
				"value": "NAMESPACEINDEX:SafetyStates"
			},
			"NodeId": {
				"type": "String",
				"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
			}
		}
	}
}
```

### key-value pairs Example

Sample uses simplified representation for data consumers `?options=keyValues`

```json
{
	"id": "MyMotionDeviceSystem",
	"type": "MotionDeviceSystem",
	"Controllers": {
		"Controller": {
			"Components": {
				"Component": {}
			},
			"Manufacturer": "Engineering Ingegneria Informatica",
			"Model": "Model",
			"ParameterSet": {
				"CPUFanSpeed": 1600.0,
				"CabinetFanSpeed": 2000.5,
				"InputVoltage": 2500.0,
				"StartUpTime": "2020-10-19T07:36:06.713Z",
				"Temperature": 50.0,
				"TotalEnergyConsumption": 170.1,
				"TotalPowerOnTime": "",
				"UPSState": "alive"
			},
			"ProductCode": "MP695ENG004",
			"SerialNumber": "ENG-004",
			"Software": {
				"MySoftware": {}
			},
			"TaskControls": {
				"TaskControl": {
					"ParameterSet": {
						"TaskProgramName": "TaskProg",
						"TaskProgramLoaded": true,
						"ExecutionMode": 0
					}
				}
			}
		}
	},
	"MotionDevices": {
		"MotionDevice": {
			"AdditionalComponents": {
				"AdditionalComponent1": {}
			},
			"Axes": {
				"AxisX": {
					"MotionProfile": 0,
					"ParameterSet": {
						"ActualPosition": 1.0,
						"ActualSpeed": 2.5,
						"ActualAcceleration": 3.0
					}
				},
				"AxisY": {
					"MotionProfile": 0,
					"ParameterSet": {
						"ActualPosition": 1.0,
						"ActualSpeed": 2.5,
						"ActualAcceleration": 3.0
					}
				}
			},
			"Manufacturer": "Engineering Ingegneria Informatica",
			"Model": "Model",
			"MotionDeviceCategory": 0,
			"PowerTrains": {
				"PowerTrain": {
					"Gears": {
						"Gears": {
							"GearRatio": 0.5,
							"Manufacturer": "Engineering Ingegneria Informatica",
							"Model": "Model",
							"Pitch": 1.0,
							"ProductCode": "MP695ENG003",
							"SerialNumber": "ENG-003"
						}
					},
					"Motors": {
						"Motor": {
							"Manufacturer": "Engineering Ingegneria Informatica",
							"Model": "Model",
							"ParameterSet": {
								"BrakeReleased": true,
								"EffectiveLoadRate": 0,
								"MotorTemperature": 75
							},
							"ProductCode": "MP695ENG002",
							"SerialNumber": "ENG-002"
						}
					}
				}
			}
		}
	},
	"SafetyStates": {
		"SafetyState": {
			"EmergencyStopFunctions": {
				"EmergencyStopFunction": {
					"Active": true,
					"Name": "emergencyStop "
				}
			},
			"ParameterSet": {
				"EmergencyStop": true,
				"OperationalMode": 0,
				"ProtectiveStop": true
			},
			"ProtectiveStopFunctions": {
				"ProtectiveStopFunction": {
					"Active": true,
					"Enabled": true,
					"Name": "protectiveStop "
				}
			}
		}
	}
}
```

### LD Example

Sample uses the NGSI-LD representation

```json
{
	"id": "urn:ngsi-ld:OPCUARoboticsCompanion:MotionDeviceSystem:MyMotionDeviceSystem",
	"type": "OPCUARoboticsCompanion:MotionDeviceSystem",
	"@context": [
		"https://schema.lab.fiware.org/ld/context",
		"https://uri.etsi.org/ngsi-ld/v1/ngsi-ld-core-context.jsonld"
	],
	"Controllers": {
		"type": "StructuredValue",
		"value": [{
			"type": "StructuredValue",
			"value": [{
					"type": "LocalizedText",
					"value": "Engineering Ingegneria Informatica",
					"metadata": {
						"BrowseName": {
							"type": "String",
							"value": "NAMESPACEINDEX:Manufacturer"
						},
						"NodeId": {
							"type": "String",
							"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
						}
					}
				},
				{
					"type": "LocalizedText",
					"value": "Model",
					"metadata": {
						"BrowseName": {
							"type": "String",
							"value": "NAMESPACEINDEX:Model"
						},
						"NodeId": {
							"type": "String",
							"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
						}
					}
				},
				{
					"type": "String",
					"value": "MP695ENG004",
					"metadata": {
						"BrowseName": {
							"type": "String",
							"value": "NAMESPACEINDEX:ProductCode"
						},
						"NodeId": {
							"type": "String",
							"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
						}
					}
				},
				{
					"type": "String",
					"value": "ENG-004",
					"metadata": {
						"BrowseName": {
							"type": "String",
							"value": "NAMESPACEINDEX:SerialNumber"
						},
						"NodeId": {
							"type": "String",
							"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
						}
					}
				},
				{
					"type": "StructuredValue",
					"value": [{
							"type": "Double",
							"value": 1600.0,
							"metadata": {
								"BrowseName": {
									"type": "String",
									"value": "NAMESPACEINDEX:CPUFanSpeed"
								},
								"NodeId": {
									"type": "String",
									"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
								}
							}
						},
						{
							"type": "Double",
							"value": 2000.5,
							"metadata": {
								"BrowseName": {
									"type": "String",
									"value": "NAMESPACEINDEX:CabinetFanSpeed"
								},
								"NodeId": {
									"type": "String",
									"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
								}
							}
						},
						{
							"type": "Double",
							"value": 2500.0,
							"metadata": {
								"BrowseName": {
									"type": "String",
									"value": "NAMESPACEINDEX:InputVoltage"
								},
								"NodeId": {
									"type": "String",
									"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
								}
							}
						},
						{
							"type": "DateTime",
							"value": "2020-10-19T07:36:06.713Z",
							"metadata": {
								"BrowseName": {
									"type": "String",
									"value": "NAMESPACEINDEX:StartUpTime"
								},
								"NodeId": {
									"type": "String",
									"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
								}
							}
						},
						{
							"type": "Double",
							"value": 50.0,
							"metadata": {
								"BrowseName": {
									"type": "String",
									"value": "NAMESPACEINDEX:Temperature"
								},
								"NodeId": {
									"type": "String",
									"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
								}
							}
						},
						{
							"type": "Double",
							"value": 170.1,
							"metadata": {
								"BrowseName": {
									"type": "String",
									"value": "NAMESPACEINDEX:TotalEnergyConsumption"
								},
								"NodeId": {
									"type": "String",
									"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
								}
							}
						},
						{
							"type": "DurationString",
							"value": "",
							"metadata": {
								"BrowseName": {
									"type": "String",
									"value": "NAMESPACEINDEX:TotalPowerOnTime"
								},
								"NodeId": {
									"type": "String",
									"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
								}
							}
						},
						{
							"type": "String",
							"value": "alive",
							"metadata": {
								"BrowseName": {
									"type": "String",
									"value": "NAMESPACEINDEX:UPSState"
								},
								"NodeId": {
									"type": "String",
									"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
								}
							}
						}
					],
					"metadata": {
						"BrowseName": {
							"type": "String",
							"value": "NAMESPACEINDEX:ParameterSet"
						},
						"NodeId": {
							"type": "String",
							"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
						}
					}
				},
				{
					"type": "StructuredValue",
					"value": [{
						"type": "StructuredValue",
						"value": {

						},
						"metadata": {
							"BrowseName": {
								"type": "String",
								"value": "NAMESPACEINDEX:Component"
							},
							"NodeId": {
								"type": "String",
								"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
							}
						}
					}],
					"metadata": {
						"BrowseName": {
							"type": "String",
							"value": "NAMESPACEINDEX:Components"
						},
						"NodeId": {
							"type": "String",
							"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
						}
					}
				},
				{
					"type": "StructuredValue",
					"value": [

					],
					"metadata": {
						"BrowseName": {
							"type": "String",
							"value": "NAMESPACEINDEX:Software"
						},
						"NodeId": {
							"type": "String",
							"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
						}
					}
				},
				{
					"type": "StructuredValue",
					"value": [{
						"type": "StructuredValue",
						"value": [{
							"type": "StructuredValue",
							"value": [{
									"type": "String",
									"value": "TaskProg",
									"metadata": {
										"BrowseName": {
											"type": "String",
											"value": "NAMESPACEINDEX:TaskProgramName"
										},
										"NodeId": {
											"type": "String",
											"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
										}
									}
								},
								{
									"type": "Boolean",
									"value": true,
									"metadata": {
										"BrowseName": {
											"type": "String",
											"value": "NAMESPACEINDEX:TaskProgramLoaded"
										},
										"NodeId": {
											"type": "String",
											"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
										}
									}
								},
								{
									"type": "Integer",
									"value": 0,
									"metadata": {
										"BrowseName": {
											"type": "String",
											"value": "NAMESPACEINDEX:ExecutionMode"
										},
										"NodeId": {
											"type": "String",
											"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
										}
									}
								}
							],
							"metadata": {
								"BrowseName": {
									"type": "String",
									"value": "NAMESPACEINDEX:ParameterSet"
								},
								"NodeId": {
									"type": "String",
									"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
								}
							}
						}],
						"metadata": {
							"BrowseName": {
								"type": "String",
								"value": "NAMESPACEINDEX:TaskControl"
							},
							"NodeId": {
								"type": "String",
								"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
							}
						}
					}],
					"metadata": {
						"BrowseName": {
							"type": "String",
							"value": "NAMESPACEINDEX:TaskControls"
						},
						"NodeId": {
							"type": "String",
							"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
						}
					}
				}
			],
			"metadata": {
				"BrowseName": {
					"type": "String",
					"value": "NAMESPACEINDEX:Controller"
				},
				"NodeId": {
					"type": "String",
					"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
				}
			}
		}],
		"metadata": {
			"BrowseName": {
				"type": "String",
				"value": "NAMESPACEINDEX:Controllers"
			},
			"NodeId": {
				"type": "String",
				"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
			}
		}
	},
	"MotionDevices": {
		"type": "StructuredValue",
		"value": [{
			"type": "StructuredValue",
			"value": [{
					"type": "LocalizedText",
					"value": "Engineering Ingegneria Informatica",
					"metadata": {
						"BrowseName": {
							"type": "String",
							"value": "NAMESPACEINDEX:Manufacturer"
						},
						"NodeId": {
							"type": "String",
							"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
						}
					}
				},
				{
					"type": "LocalizedText",
					"value": "Model",
					"metadata": {
						"BrowseName": {
							"type": "String",
							"value": "NAMESPACEINDEX:Model"
						},
						"NodeId": {
							"type": "String",
							"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
						}
					}
				},
				{
					"type": "String",
					"value": "MP695ENG004",
					"metadata": {
						"BrowseName": {
							"type": "String",
							"value": "NAMESPACEINDEX:ProductCode"
						},
						"NodeId": {
							"type": "String",
							"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
						}
					}
				},
				{
					"type": "String",
					"value": "ENG-004",
					"metadata": {
						"BrowseName": {
							"type": "String",
							"value": "NAMESPACEINDEX:SerialNumber"
						},
						"NodeId": {
							"type": "String",
							"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
						}
					}
				},
				{
					"type": "Integer",
					"value": 0,
					"metadata": {
						"BrowseName": {
							"type": "String",
							"value": "NAMESPACEINDEX:MotionDeviceCategory"
						},
						"NodeId": {
							"type": "String",
							"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
						}
					}
				},
				{
					"type": "StructuredValue",
					"value": [{
						"type": "StructuredValue",
						"value": {},
						"metadata": {
							"BrowseName": {
								"type": "String",
								"value": "NAMESPACEINDEX:AdditionalComponent"
							},
							"NodeId": {
								"type": "String",
								"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
							}
						}
					}],
					"metadata": {
						"BrowseName": {
							"type": "String",
							"value": "NAMESPACEINDEX:AdditionalComponents"
						},
						"NodeId": {
							"type": "String",
							"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
						}
					}
				},
				{
					"type": "StructuredValue",
					"value": [{
							"type": "StructuredValue",
							"value": [{
									"type": "Integer",
									"value": 0,
									"metadata": {
										"BrowseName": {
											"type": "String",
											"value": "NAMESPACEINDEX:MotionProfile"
										},
										"NodeId": {
											"type": "String",
											"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
										}
									}
								},
								{
									"type": "StructuredValue",
									"value": [{
											"type": "Double",
											"value": 15.0,
											"metadata": {
												"BrowseName": {
													"type": "String",
													"value": "NAMESPACEINDEX:ActualPosition"
												},
												"NodeId": {
													"type": "String",
													"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
												}
											}
										},
										{
											"type": "Double",
											"value": 1.0,
											"metadata": {
												"BrowseName": {
													"type": "String",
													"value": "NAMESPACEINDEX:ActualSpeed"
												},
												"NodeId": {
													"type": "String",
													"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
												}
											}
										},
										{
											"type": "Double",
											"value": 0.5,
											"metadata": {
												"BrowseName": {
													"type": "String",
													"value": "NAMESPACEINDEX:ActualAcceleration"
												},
												"NodeId": {
													"type": "String",
													"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
												}
											}
										}
									],
									"metadata": {
										"BrowseName": {
											"type": "String",
											"value": "NAMESPACEINDEX:ParameterSet"
										},
										"NodeId": {
											"type": "String",
											"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
										}
									}
								}
							],
							"metadata": {
								"BrowseName": {
									"type": "String",
									"value": "NAMESPACEINDEX:AxisX"
								},
								"NodeId": {
									"type": "String",
									"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
								}
							}
						},
						{
							"type": "StructuredValue",
							"value": [{
									"type": "Integer",
									"value": 0,
									"metadata": {
										"BrowseName": {
											"type": "String",
											"value": "NAMESPACEINDEX:MotionProfile"
										},
										"NodeId": {
											"type": "String",
											"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
										}
									}
								},
								{
									"type": "StructuredValue",
									"value": [{
											"type": "Double",
											"value": 15.0,
											"metadata": {
												"BrowseName": {
													"type": "String",
													"value": "NAMESPACEINDEX:ActualPosition"
												},
												"NodeId": {
													"type": "String",
													"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
												}
											}
										},
										{
											"type": "Double",
											"value": 1.0,
											"metadata": {
												"BrowseName": {
													"type": "String",
													"value": "NAMESPACEINDEX:ActualSpeed"
												},
												"NodeId": {
													"type": "String",
													"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
												}
											}
										},
										{
											"type": "Double",
											"value": 0.5,
											"metadata": {
												"BrowseName": {
													"type": "String",
													"value": "NAMESPACEINDEX:ActualAcceleration"
												},
												"NodeId": {
													"type": "String",
													"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
												}
											}
										}
									],
									"metadata": {
										"BrowseName": {
											"type": "String",
											"value": "NAMESPACEINDEX:ParameterSet"
										},
										"NodeId": {
											"type": "String",
											"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
										}
									}
								}
							],
							"metadata": {
								"BrowseName": {
									"type": "String",
									"value": "NAMESPACEINDEX:AxisY"
								},
								"NodeId": {
									"type": "String",
									"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
								}
							}
						}
					],
					"metadata": {
						"BrowseName": {
							"type": "String",
							"value": "NAMESPACEINDEX:Axes"
						},
						"NodeId": {
							"type": "String",
							"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
						}
					}
				},
				{
					"type": "StructuredValue",
					"value": [{
							"type": "Boolean",
							"value": true,
							"metadata": {
								"BrowseName": {
									"type": "String",
									"value": "NAMESPACEINDEX:OnPath"
								},
								"NodeId": {
									"type": "String",
									"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
								}
							}
						},
						{
							"type": "Boolean",
							"value": true,
							"metadata": {
								"BrowseName": {
									"type": "String",
									"value": "NAMESPACEINDEX:InControl"
								},
								"NodeId": {
									"type": "String",
									"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
								}
							}
						},
						{
							"type": "Double",
							"value": 0.5,
							"metadata": {
								"BrowseName": {
									"type": "String",
									"value": "NAMESPACEINDEX:SpeedOverride"
								},
								"NodeId": {
									"type": "String",
									"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
								}
							}
						}
					],
					"metadata": {
						"BrowseName": {
							"type": "String",
							"value": "NAMESPACEINDEX:ParameterSet"
						},
						"NodeId": {
							"type": "String",
							"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
						}
					}
				},
				{
					"type": "StructuredValue",
					"value": [{
						"type": "StructuredValue",
						"value": [{
								"type": "StructuredValue",
								"value": [{
									"type": "StructuredValue",
									"value": [{
											"type": "LocalizedText",
											"value": "Engineering Ingegneria Informatica",
											"metadata": {
												"BrowseName": {
													"type": "String",
													"value": "NAMESPACEINDEX:Manufacturer"
												},
												"NodeId": {
													"type": "String",
													"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
												}
											}
										},
										{
											"type": "LocalizedText",
											"value": "Model",
											"metadata": {
												"BrowseName": {
													"type": "String",
													"value": "NAMESPACEINDEX:Model"
												},
												"NodeId": {
													"type": "String",
													"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
												}
											}
										},
										{
											"type": "String",
											"value": "MP695ENG003",
											"metadata": {
												"BrowseName": {
													"type": "String",
													"value": "NAMESPACEINDEX:ProductCode"
												},
												"NodeId": {
													"type": "String",
													"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
												}
											}
										},
										{
											"type": "String",
											"value": "ENG-003",
											"metadata": {
												"BrowseName": {
													"type": "String",
													"value": "NAMESPACEINDEX:SerialNumber"
												},
												"NodeId": {
													"type": "String",
													"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
												}
											}
										},
										{
											"type": "Double",
											"value": "0.25",
											"metadata": {
												"BrowseName": {
													"type": "String",
													"value": "NAMESPACEINDEX:GearRatio"
												},
												"NodeId": {
													"type": "String",
													"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
												}
											}
										},
										{
											"type": "Double",
											"value": "1.5",
											"metadata": {
												"BrowseName": {
													"type": "String",
													"value": "NAMESPACEINDEX:Pitch"
												},
												"NodeId": {
													"type": "String",
													"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
												}
											}
										}
									],
									"metadata": {
										"BrowseName": {
											"type": "String",
											"value": "NAMESPACEINDEX:Gear"
										},
										"NodeId": {
											"type": "String",
											"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
										}
									}
								}],
								"metadata": {
									"BrowseName": {
										"type": "String",
										"value": "NAMESPACEINDEX:Gears"
									},
									"NodeId": {
										"type": "String",
										"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
									}
								}
							},
							{
								"type": "StructuredValue",
								"value": [{
									"type": "StructuredValue",
									"value": [{
											"type": "LocalizedText",
											"value": "Engineering Ingegneria Informatica",
											"metadata": {
												"BrowseName": {
													"type": "String",
													"value": "NAMESPACEINDEX:Manufacturer"
												},
												"NodeId": {
													"type": "String",
													"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
												}
											}
										},
										{
											"type": "LocalizedText",
											"value": "Model",
											"metadata": {
												"BrowseName": {
													"type": "String",
													"value": "NAMESPACEINDEX:Model"
												},
												"NodeId": {
													"type": "String",
													"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
												}
											}
										},
										{
											"type": "String",
											"value": "MP695ENG002",
											"metadata": {
												"BrowseName": {
													"type": "String",
													"value": "NAMESPACEINDEX:ProductCode"
												},
												"NodeId": {
													"type": "String",
													"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
												}
											}
										},
										{
											"type": "String",
											"value": "ENG-002",
											"metadata": {
												"BrowseName": {
													"type": "String",
													"value": "NAMESPACEINDEX:SerialNumber"
												},
												"NodeId": {
													"type": "String",
													"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
												}
											}
										},
										{
											"type": "StructuredValue",
											"value": [{
													"type": "Boolean",
													"value": true,
													"metadata": {
														"BrowseName": {
															"type": "String",
															"value": "NAMESPACEINDEX:BrakeReleased"
														},
														"NodeId": {
															"type": "String",
															"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
														}
													}
												},
												{
													"type": "Double",
													"value": 75.0,
													"metadata": {
														"BrowseName": {
															"type": "String",
															"value": "NAMESPACEINDEX:motorTemperature"
														},
														"NodeId": {
															"type": "String",
															"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
														}
													}
												},
												{
													"type": "Integer",
													"value": 0,
													"metadata": {
														"BrowseName": {
															"type": "String",
															"value": "NAMESPACEINDEX:EffectiveLoadRate"
														},
														"NodeId": {
															"type": "String",
															"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
														}
													}
												}
											],
											"metadata": {
												"BrowseName": {
													"type": "String",
													"value": "NAMESPACEINDEX:ParameterSet"
												},
												"NodeId": {
													"type": "String",
													"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
												}
											}
										}
									],
									"metadata": {
										"BrowseName": {
											"type": "String",
											"value": "NAMESPACEINDEX:Motor"
										},
										"NodeId": {
											"type": "String",
											"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
										}
									}
								}],
								"metadata": {
									"BrowseName": {
										"type": "String",
										"value": "NAMESPACEINDEX:Motors"
									},
									"NodeId": {
										"type": "String",
										"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
									}
								}
							}
						],
						"metadata": {
							"BrowseName": {
								"type": "String",
								"value": "NAMESPACEINDEX:PowerTrain"
							},
							"NodeId": {
								"type": "String",
								"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
							}
						}
					}],
					"metadata": {
						"BrowseName": {
							"type": "String",
							"value": "NAMESPACEINDEX:PowerTrains"
						},
						"NodeId": {
							"type": "String",
							"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
						}
					}
				}
			],
			"metadata": {
				"BrowseName": {
					"type": "String",
					"value": "NAMESPACEINDEX:MotionDevice"
				},
				"NodeId": {
					"type": "String",
					"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
				}
			}
		}],
		"metadata": {
			"BrowseName": {
				"type": "String",
				"value": "NAMESPACEINDEX:MotionDevices"
			},
			"NodeId": {
				"type": "String",
				"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
			}
		}
	},
	"SafetyStates": {
		"type": "StructuredValue",
		"value": [{
			"type": "StructuredValue",
			"value": [{
					"type": "StructuredValue",
					"value": [{
							"type": "Integer",
							"value": 0,
							"metadata": {
								"BrowseName": {
									"type": "String",
									"value": "NAMESPACEINDEX:OperationalMode"
								},
								"NodeId": {
									"type": "String",
									"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
								}
							}
						},
						{
							"type": "Boolean",
							"value": true,
							"metadata": {
								"BrowseName": {
									"type": "String",
									"value": "NAMESPACEINDEX:ProtectiveStop"
								},
								"NodeId": {
									"type": "String",
									"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
								}
							}
						},
						{
							"type": "Boolean",
							"value": true,
							"metadata": {
								"BrowseName": {
									"type": "String",
									"value": "NAMESPACEINDEX:EmergencyStop"
								},
								"NodeId": {
									"type": "String",
									"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
								}
							}
						}
					],
					"metadata": {
						"BrowseName": {
							"type": "String",
							"value": "NAMESPACEINDEX:ParameterSet"
						},
						"NodeId": {
							"type": "String",
							"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
						}
					}
				},
				{
					"type": "StructuredValue",
					"value": [{
						"type": "StructuredValue",
						"value": [{
								"type": "String",
								"value": "EmergencyStopFunc",
								"metadata": {
									"BrowseName": {
										"type": "String",
										"value": "NAMESPACEINDEX:name"
									},
									"NodeId": {
										"type": "String",
										"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
									}
								}
							},
							{
								"type": "Boolean",
								"value": true,
								"metadata": {
									"BrowseName": {
										"type": "String",
										"value": "NAMESPACEINDEX:Active"
									},
									"NodeId": {
										"type": "String",
										"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
									}
								}
							}
						],
						"metadata": {
							"BrowseName": {
								"type": "String",
								"value": "NAMESPACEINDEX:EmergencyStopFunction"
							},
							"NodeId": {
								"type": "String",
								"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
							}
						}
					}],
					"metadata": {
						"BrowseName": {
							"type": "String",
							"value": "NAMESPACEINDEX:EmergencyStopFunctions"
						},
						"NodeId": {
							"type": "String",
							"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
						}
					}
				},
				{
					"type": "StructuredValue",
					"value": [{
						"type": "StructuredValue",
						"value": [{
								"type": "String",
								"value": "ProtectiveStopFunc",
								"metadata": {
									"BrowseName": {
										"type": "String",
										"value": "NAMESPACEINDEX:name"
									},
									"NodeId": {
										"type": "String",
										"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
									}
								}
							},
							{
								"type": "Boolean",
								"value": true,
								"metadata": {
									"BrowseName": {
										"type": "String",
										"value": "NAMESPACEINDEX:Active"
									},
									"NodeId": {
										"type": "String",
										"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
									}
								}
							},
							{
								"type": "Boolean",
								"value": true,
								"metadata": {
									"BrowseName": {
										"type": "String",
										"value": "NAMESPACEINDEX:Enabled"
									},
									"NodeId": {
										"type": "String",
										"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
									}
								}
							}
						],
						"metadata": {
							"BrowseName": {
								"type": "String",
								"value": "NAMESPACEINDEX:ProtectiveStopFunction"
							},
							"NodeId": {
								"type": "String",
								"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
							}
						}
					}],
					"metadata": {
						"BrowseName": {
							"type": "String",
							"value": "NAMESPACEINDEX:ProtectiveStopFunctions"
						},
						"NodeId": {
							"type": "String",
							"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
						}
					}
				}
			],
			"metadata": {
				"BrowseName": {
					"type": "String",
					"value": "NAMESPACEINDEX:SafetyState"
				},
				"NodeId": {
					"type": "String",
					"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
				}
			}
		}],
		"metadata": {
			"BrowseName": {
				"type": "String",
				"value": "NAMESPACEINDEX:SafetyStates"
			},
			"NodeId": {
				"type": "String",
				"value": "ns:NAMESPACEINDEX,i=IDENTIFIER"
			}
		}
	}
}
```
