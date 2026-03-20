# Table Design

## users
- id (UUID, PK)
- lineworks_user_id (unique)
- name
- email
- role (employee / manager / admin)
- dept_id
- manager_user_id
- is_active
- created_at
- updated_at

---

## departments
- id
- dept_code
- dept_name
- created_at
- updated_at

---

## attendance_entries
- id
- user_id
- work_date
- work_type_id
- leave_type_id
- start_time
- end_time
- break_minutes
- note
- is_holiday
- row_version
- created_at
- updated_at

unique(user_id, work_date)

---

## monthly_closings
- id
- user_id
- year_month
- status (open / closed)
- closed_by
- closed_at
- unclosed_by
- unclosed_at
- created_at
- updated_at

unique(user_id, year_month)

---

## freee_links
- id
- user_id (unique)
- is_configured
- freee_user_key
- access_token_enc
- refresh_token_enc
- token_expires_at
- last_linked_at
- created_at
- updated_at

---

## sync_jobs
- id
- user_id
- job_type (month / day)
- year_month
- work_date
- status (unsent / sent / failed / retry_wait)
- error_message
- requested_at
- sent_at
- created_at
- updated_at

---

## audit_logs
- id
- actor_user_id
- target_type
- target_id
- action
- changed_fields_json
- created_at

---

## operation_logs
- id
- actor_user_id
- operation
- ip_address
- user_agent
- meta_json
- created_at