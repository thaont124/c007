# eTom: Track & Manage  Service Provisioning

1. update CFSOrderItem (state = inProgress)
2. validate tất cả các trường của service order
	+ Date.now() <= orderDate <= requestedStartDate <= completionDate <= cancellationDate
3. POST /checkServiceQualification (tmf645)
	+ Duyệt qua toàn bộ serviceOrderItem
	+ tổng hợp toàn bộ serviceOrderItem.service  thành 1 list A
	+ checkServiceQualification.setService(A)
		service order			check Service Qualification
		expectedCompletionDate		exxpectedQualificationDate
		externalId			extenalId
		relatedParty			relatedParty
	+ POST /checkServiceQualification
<i><sub>   
599 - Service Order Tracking ??????? có cần check qua sau khi POST checkServiceQualification ???? 
	+ trackServiceOrder nhận kết quả từ POST /checkServiceQualification.
	+ generateEventId tạo ID cho sự kiện.
	+ updateServiceOrderLifecycle cập nhật trạng thái Service Order:
		TH1 (qualified): Chuyển sang "inProgress".
		TH2 (notQualified): Chuyển sang "onHold".
	+ updateServiceOrderItems cập nhật trạng thái các Service Order Items:
		TH1: Chuyển sang "inProgress".
		TH2: Chuyển sang "onHold".
	+ handleAlternateServiceProposal xử lý đề xuất thay thế:
		TH1: Bỏ qua.
		TH2: Thông báo đề xuất thay thế qua EventPublisher.
</i></sub>

4. Allocate Specific Service (chưa làm)
	4.1. POST /service
	4.2. TMF633 - GET /serviceSpecification
	Lấy thông tin CFS bao gồm RFS
	Sau đó tiếp tục lấy thông tin RFS bao gồm RS

	4.3. Lấy thông tin RS
	TMF638 - POST /service
	Gửi thông tin RFS

	592 - Service Parameter Reservation
	Cập nhật trạng thái (state)

	591 - Service Parameter Allocation
	Cập nhật trạng thái (state)	

7. 596 - Service Order Transfer Supervision
	
8. Implement, Configure & Activate Service (chưa làm)
	
5. 599 - Service Order Tracking
	+ 
6. 596 - Service Order Transfer Supervision

7. 598 - Service Order Orchestration

8. 733 Service Order Decomposition

9. POST /resourceOrder (tmf652)




CheckServiceQualification # c007
