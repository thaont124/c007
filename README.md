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
4. Allocate Specific Service (chưa làm)
	
5. 599 - Service Order Tracking ??????? có cần check qua sau khi checkServiceQualification
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
6. 596 - Service Order Transfer Supervision
	
7. Implement, Configure & Activate Service (chưa làm)
	
5. 599 - Service Order Tracking
	+ 
6. 596 - Service Order Transfer Supervision

7. 598 - Service Order Orchestration

8. 733 Service Order Decomposition

9. POST /resourceOrder (tmf652)




CheckServiceQualification # c007
