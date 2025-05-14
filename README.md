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

5. 599 - Service Order Tracking
	+ 
6. 596 - Service Order Transfer Supervision

7. Implement, Configure & Activate Service (chưa làm)

5. 599 - Service Order Tracking
	+ 
6. 596 - Service Order Transfer Supervision

7. 598 - Service Order Orchestration

8. 733 Service Order Decomposition

9. POST /resourceOrder




CheckServiceQualification # c007
